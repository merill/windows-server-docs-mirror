---
layout: Conceptual
title: Develop an extension for Windows Admin Center | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/developing-extensions
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Develop an extension for Windows Admin Center SDK (Project Honolulu)
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-09-19T00:00:00.0000000Z
locale: en-us
document_id: b735475f-9a5c-df89-da05-b7f626304460
document_version_independent_id: 132063e8-c677-733d-c1ed-4de93c9a6951
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/developing-extensions.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/developing-extensions
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/developing-extensions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 53548054-35fb-d4eb-4950-a9b78dc047ea
---

# Develop an extension for Windows Admin Center | Microsoft Learn

Windows Admin Center supports three types of extensions - tool extensions, solution extensions and gateway plugins. The SDK contains content and examples to guide you in building the different types of extensions/plugins.

Note

Not familiar with the different extension types? Learn more about the [extensibility architecture and extension types](understand-extensions).

## Development step-by-step

- [Prepare](prepare-development-environment) your development environment
- Create a [tool](develop-tool) extension
- Create a [solution](develop-solution) extension
- Create a [gateway plugin](develop-gateway-plugin)
- Learn more with our [guides](guides)

## SDK design toolkit

Check out our Windows Admin Center [SDK design toolkit](https://github.com/Microsoft/windows-admin-center-sdk/blob/master/WindowsAdminCenterDesignToolkit.zip)! This toolkit is designed to help you rapidly mock up extensions in PowerPoint using Windows Admin Center styles, controls, and page templates. See what your extension can look like in Windows Admin Center before you start coding!