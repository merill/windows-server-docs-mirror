---
layout: Conceptual
title: Target a different version of the Windows Admin Center SDK | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/target-sdk-version
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Target a different version of the Windows Admin Center SDK (Project Honolulu)
ms.topic: how-to
author: davannaw-msft
ms.author: dawhite
ms.date: 2018-09-18T00:00:00.0000000Z
locale: en-us
document_id: 0e06996a-3b81-3f1d-2c24-d91a9add306d
document_version_independent_id: 357360cd-b855-03bc-66fa-71c2c28e17e9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/target-sdk-version.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/target-sdk-version
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/target-sdk-version.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: d6b3a3f4-4ce2-01cc-cad7-3d14a92f24b2
---

# Target a different version of the Windows Admin Center SDK | Microsoft Learn

Keeping your extension up to date with SDK changes and platform changes is easy. We use [NuGet Package Manager tags](https://www.npmjs.com/package/@microsoft/windows-admin-center-sdk?activeTab=versions) to organize the release of new features into SDK versions.

There are two SDK versions you can choose from and three which are deprecated:

- `latest` – this SDK package aligns with the current GA release of Windows Admin Center and is the most stable
- `experimental` – this SDK package contains the most recent changes and functionality, but might be unstable
- `insider` – this SDK package has been deprecated, use latest or experimental instead
- `next` – this SDK package has been deprecated, use latest or experimental instead
- `legacy` – this SDK package has been deprecated, use latest or experimental instead

Note

Find out more about the different [versions](../overview) of Windows Admin Center that are available to download.

## Targeting SDK version on a new project

When creating a new extension, you can include the `--version` parameter to target a different version of the SDK:

```
wac create --company "{!Company Name}" --tool "{!Tool Name}" --version {!version}
```

| Value | Explanation | Example |
| --- | --- | --- |
| `{!Company Name}` | Your company name (with spaces) | `Contoso Inc` |
| `{!Tool Name}` | Your tool name (with spaces) | `Manage Foo Works` |
| `{!version}` | SDK Version | `latest` |

Here's an example creating a new extension targeting `experimental`:

```
wac create --company "Contoso Inc" --tool "Manage Foo Works" --version experimental
```

Note

We recommend developers building new extensions use the `latest` SDK version for stability.

## Targeting SDK version on an existing project

To modify an existing project to target a different SDK version, modify the following line in `package.json`:

```
"@microsoft/windows-admin-center-sdk": "latest",
```

In this example, replace `latest` with your desired SDK version, i.e. `experimental`:

```
"@microsoft/windows-admin-center-sdk": "experimental",
```

Then run `npm install` to update references throughout your project.