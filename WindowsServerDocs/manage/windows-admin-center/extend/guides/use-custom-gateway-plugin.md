---
layout: Conceptual
title: Use a custom gateway plugin in your tool extension | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/guides/use-custom-gateway-plugin
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Develop a tool extension Windows Admin Center SDK (Project Honolulu) - use a custom gateway plugin in your tool extension
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2018-09-18T00:00:00.0000000Z
locale: en-us
document_id: fd7fda5a-a293-4411-fd99-9c795b8acb45
document_version_independent_id: 4f153128-00ee-9093-5e55-7d013490f1a6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/guides/use-custom-gateway-plugin.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/guides/use-custom-gateway-plugin
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/guides/use-custom-gateway-plugin.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 23f45d01-e1fa-fd56-a247-3438b4d699d7
---

# Use a custom gateway plugin in your tool extension | Microsoft Learn

In this article, we will use a custom gateway plugin in a new, empty tool extension we have created with the Windows Admin Center CLI.

## Prepare your environment

If you haven't already, follow the directions in [develop a tool extension](../develop-tool) to prepare your environment and create a new, empty tool extension.

## Add a module to your project

If you haven't already, add a new [empty module](add-module) to your project, which we will use in the next step.

## Add integration to custom gateway plugin

Now we'll use a custom gateway plugin in the new, empty module that we just created.

### Create plugin.service.ts

Change to the directory of the new tool module created above (`\src\app\{!Module-Name}`), and create a new file `plugin.service.ts`.

Add the following code to the file just created:

```ts
import { Injectable } from '@angular/core';
import { AppContextService, HttpService } from '@microsoft/windows-admin-center-sdk/angular';
import { Cim, Http, PowerShell, PowerShellSession } from '@microsoft/windows-admin-center-sdk/core';
import { AjaxResponse, Observable } from 'rxjs';

@Injectable()
export class PluginService {
    constructor(private appContextService: AppContextService, private http: Http) {
    }

    public getGatewayRestResponse(): Observable<any> {
        let callUrl = this.appContextService.activeConnection.nodeName;

        return this.appContextService.node.get(callUrl, 'features/Sample%20Uno').map(
            (response: any) => {
                return response;
            }
        )
    }
}
```

Change references to `Sample Uno` and `Sample%20Uno` to your feature name as appropriate.

Warning

It is recommended that the built in `this.appContextService.node` is used for calling any API that is defined in your custom gateway plugin. This will ensure that if credentials are required inside of your gateway plugin that they will be handled properly.

### Modify module.ts

Open the `module.ts` file of the new module created earlier (i.e. `{!Module-Name}.module.ts`):

Add the following import statements:

```ts
import { HttpService } from '@microsoft/windows-admin-center-sdk/angular';
import { Http } from '@microsoft/windows-admin-center-sdk/core';
import { PluginService } from './plugin.service';
```

Add the following providers (after declarations):

```ts
  ,
  providers: [
    HttpService,
    PluginService,
    Http
  ]
```

### Modify component.ts

Open the `component.ts` file of the new module created earlier (i.e. `{!Module-Name}.component.ts`):

Add the following import statements:

```ts
import { ActivatedRouteSnapshot } from '@angular/router';
import { AppContextService } from '@microsoft/windows-admin-center-sdk/angular';
import { Subscription } from 'rxjs';
import { Strings } from '../../generated/strings';
import { PluginService } from './plugin.service';
```

Add the following variables:

```ts
  private serviceSubscription: Subscription;
  private responseResult: string;
```

Modify the constructor and modify/add the following functions:

```ts
  constructor(private appContextService: AppContextService, private plugin: PluginService) {
    //
  }

  public ngOnInit() {
    this.responseResult = 'click go to do something';
  }

  public onClick() {
    this.serviceSubscription = this.plugin.getGatewayRestResponse().subscribe(
      (response: any) => {
        this.responseResult = 'response: ' + response.message;
      },
      (error) => {
        console.log(error);
      }
    );
  }
```

### Modify component.html

Open the `component.html` file of the new module created earlier (i.e. `{!Module-Name}.component.html`):

Add the following content to the html file:

```html
<button (click)="onClick()" >go</button>
{{ responseResult }}
```

## Build and side load your extension

Now you are ready to [build and side load](../develop-tool#build-and-side-load-your-extension) your extension in Windows Admin Center.