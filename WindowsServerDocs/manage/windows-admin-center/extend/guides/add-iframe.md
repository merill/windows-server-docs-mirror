---
layout: Conceptual
title: Add an iFrame to a tool extension | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/guides/add-iframe
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Develop a tool extension Windows Admin Center SDK (Project Honolulu) - add an iFrame to a tool extension
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2018-09-18T00:00:00.0000000Z
locale: en-us
document_id: d2a683bc-42e9-5309-3946-2f7c7f739625
document_version_independent_id: 5106e4e7-cbb2-016d-f362-e2c7040c3184
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/guides/add-iframe.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/guides/add-iframe
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/guides/add-iframe.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 522210df-3bdd-7b66-4e4c-5956e5901c50
---

# Add an iFrame to a tool extension | Microsoft Learn

In this article, we will add an iFrame to a new, empty tool extension we have created with the Windows Admin Center CLI.

## Prepare your environment

If you haven't already, follow the directions in [develop a tool extension](../develop-tool) to prepare your environment and create a new, empty tool extension.

## Add a module to your project

Add a new [empty module](add-module) to your project, to which we will add an iFrame in the next step.

## Add an iFrame to your module

Now we'll add an iFrame to that new, empty module that we just created.

In \src\app, browse into your module folder, then open file `{!module-name}.component.html`, found with the following naming convention:

| Value | Explanation | Example filename |
| --- | --- | --- |
| `{!module-name}` | Your module name (lower case, spaces replaced with dashes) | `manage-foo-works-portal.component.html` |

Add the following content to the html file:

```html
<div>
  <iframe  style="height: 850px;" src="https://www.bing.com"></iframe>
</div>
```

That's it, you've added an iFrame to your extension. Next, you can [build and side load](../develop-tool#build-and-side-load-your-extension) your extension in Windows Admin Center to see the results.

Note

Content Security Policy (CSP) settings could prevent some sites from rendering in an iFrame within Windows Admin Center. You can learn more about this [here](https://content-security-policy.com/).