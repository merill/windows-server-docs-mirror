---
layout: Conceptual
title: Guides | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/guides
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Guides Windows Admin Center SDK (Project Honolulu)
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2018-09-17T00:00:00.0000000Z
locale: en-us
document_id: cf22a13d-288a-f45d-d396-0eda333c2f1e
document_version_independent_id: 4b3c1441-b8e6-896e-d23d-07697d38e29e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/guides.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/guides
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/guides.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: cd985c5e-a478-fd52-087b-6c1ef673f9bb
---

# Guides | Microsoft Learn

## Guides

Here are some guides for developing with the Windows Admin Center SDK:

- [Add a module to a tool extension](guides/add-module)
- [Add an iFrame to a tool extension](guides/add-iframe)
- [Use a custom gateway plugin in your tool extension](guides/use-custom-gateway-plugin)
- [Create a connection provider](guides/create-connection-provider)
- [Modify root navigation behavior](guides/modify-root-navigation)
- [Control your tool's visibility](guides/dynamic-tool-display)
- [Strings and localization](guides/strings-localization)
- [Using PowerShell in your extension](guides/powershell)
- [CSS icon guide](guides/cssicons)

## SDK design toolkit

- Check out our Windows Admin Center [SDK design toolkit](https://github.com/Microsoft/windows-admin-center-sdk/blob/master/WindowsAdminCenterDesignToolkit.zip)! This toolkit is designed to help you rapidly mock up extensions in PowerPoint using Windows Admin Center styles, controls, and page templates. See what your extension can look like in Windows Admin Center before you start coding!

## Sample code included with the SDK

- Sample code can be found for [tool](develop-tool), [solution](develop-solution), and [gateway plugin](develop-gateway-plugin) extension types in our SDK documentation. There you will leverage the Windows Admin Center CLI to build a new extension project, then follow the individual guides to customize your project to meet your needs.
- [Developer Tools](https://aka.ms/wacsdk), hosted on our GitHub SDK site, is a solution extension containing a rich collection of controls that you can browse and use in your own extension. Developer Tools is a fully functioning extension that can be side-loaded into Windows Admin Center in Developer Mode.