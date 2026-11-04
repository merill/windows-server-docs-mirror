---
layout: Conceptual
title: Install extension payload on a managed node | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/guides/install-on-node
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Instructions about how to install extension payload on a managed node
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2018-09-18T00:00:00.0000000Z
locale: en-us
document_id: e529d738-13b1-00fd-a837-da14b48b26be
document_version_independent_id: 9120f876-2d83-7d32-a4b6-d284cafe7a9a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/guides/install-on-node.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/guides/install-on-node
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/guides/install-on-node.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 968a1426-a0f0-5888-6b3d-8d270b263fb8
---

# Install extension payload on a managed node | Microsoft Learn

## Setup

Note

To follow this guide, you will need build 1.2.1904.02001 or higher. To check your build number open Windows Admin Center and click the question mark in the top right.

If you haven't already, create a [tool extension](../develop-tool) for Windows Admin Center. After you have completed this make note of the values used when creating an extension:

| Value | Explanation | Example |
| --- | --- | --- |
| `{!Company Name}` | Your company name (with spaces) | `Contoso` |
| `{!Tool Name}` | Your tool name (with spaces) | `InstallOnNode` |

Inside your tool extension folder create a `Node` folder (`{!Tool Name}\Node`). Anything placed in this folder will be copied to the managed node when using this API. Add any files necessary for your use case.

Also create a `{!Tool Name}\Node\installNode.ps1` script. This script will be ran on the managed node once all files are copied from the `{!Tool Name}\Node` folder to the managed node. Add any additional logic for your use case. An example `{!Tool Name}\Node\installNode.ps1` file:

```ps1
# Add logic for installing payload on managed node
echo 'Success'
```

Note

`{!Tool Name}\Node\installNode.ps1` has a specific name that the API will look for. Changing the name of this file will cause an error.

## Integration with UI

Update `\src\app\default.component.ts` to the following:

```ts
import { Component } from '@angular/core';
import { AppContextService } from '@microsoft/windows-admin-center-sdk/angular';
import { Observable } from 'rxjs';

@Component({
  selector: 'default-component',
  templateUrl: './default.component.html',
  styleUrls: ['./default.component.css']
})

export class DefaultComponent {
  constructor(private appContextService: AppContextService) { }

  public response: any;
  public loading = false;

  public installOnNode() {
    this.loading = true;
    this.post('{!Company Name}.{!Tool Name}', '1.0.0',
      this.appContextService.activeConnection.nodeName).subscribe(
        (response: any) => {
          console.log(response);
          this.response = response;
          this.loading = false;
        },
        (error) => {
          console.log(error);
          this.response = error;
          this.loading = false;
        }
      );
  }

  public post(id: string, version: string, targetNode: string): Observable<any> {
    return this.appContextService.node.post(targetNode,
      `features/extensions/${id}/versions/${version}/install`);
  }

}
```

Update placeholders to values that were used when creating the extension:

```ts
this.post('contoso.install-on-node', '1.0.0',
      this.appContextService.activeConnection.nodeName).subscribe(
        (response: any) => {
          console.log(response);
          this.response = response;
          this.loading = false;
        },
        (error) => {
          console.log(error);
          this.response = error;
          this.loading = false;
        }
      );
```

Also update `\src\app\default.component.html` to:

```html
<button (click)="installOnNode()">Click to install</button>
<sme-loading-wheel *ngIf="loading" size="large"></sme-loading-wheel>
<p *ngIf="response">{{response}}</p>
```

And lastly `\src\app\default.module.ts`:

```ts
import { CommonModule } from '@angular/common';
import { NgModule } from '@angular/core';

import { LoadingWheelModule } from '@microsoft/windows-admin-center-sdk/angular';
import { DefaultComponent } from './default.component';
import { Routing } from './default.routing';

@NgModule({
  imports: [
    CommonModule,
    LoadingWheelModule,
    Routing
  ],
  declarations: [DefaultComponent]
})
export class DefaultModule { }

```

## Creating and installing a NuGet Package

The last step is building a NuGet package with the files we have added and then installing that package in Windows Admin Center.

Follow the [Publishing Extensions](../publish-extensions) guide if you have not created an extension package before.

Important

In your .nuspec file for this extension, it is important that the `<id>` value matches the name in your project's `manifest.json` and the `<version>` matches what was added to `\src\app\default.component.ts`. Also add an entry under `<files>`:

`<file src="Node\**\*.*" target="Node" />`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<package xmlns="https://schemas.microsoft.com/packaging/2011/08/nuspec.xsd">
  <metadata>
    <id>contoso.install-on-node</id>
    <version>1.0.0</version>
    <authors>Contoso</authors>
    <owners>Contoso</owners>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <projectUrl>https://msft-sme.myget.org/feed/windows-admin-center-feed/package/nuget/contoso.sme.install-on-node-extension</projectUrl>
    <licenseUrl>http://YourLicenseLink</licenseUrl>
    <iconUrl>http://YourLogoLink</iconUrl>
    <description>Install on node extension by Contoso</description>
    <copyright>(c) Contoso. All rights reserved.</copyright>
  </metadata>
    <files>
    <file src="bundle\**\*.*" target="ux" />
    <file src="package\**\*.*" target="gateway" />
    <file src="Node\**\*.*" target="Node" />
  </files>
</package>
```

Once this package is created, add a path to that feed. In Windows Admin Center go to Settings &gt; Extensions &gt; Feeds and add the path to where that package exists. When your extension is done being installed, you should be able to click the `install` button and the API will be called.