---
layout: Conceptual
title: Prehash and Preload Content on the Hosted Cache Server (Optional) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/bc-hcm/7-bc-prehash-preload
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to prehash content on your content servers, add the content to data packages, and then preload the content on your hosted cache servers.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 36a9a2d9-1784-4951-7916-7a20fb511851
document_version_independent_id: 7b84cdaa-bd11-f110-28f9-dcea1cbbfd48
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/7-Bc-Prehash-Preload.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/bc-hcm/7-bc-prehash-preload
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/7-Bc-Prehash-Preload.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 4e431471-5e42-8d5c-f9e9-4bf39902409d
---

# Prehash and Preload Content on the Hosted Cache Server (Optional) | Microsoft Learn

You can use the procedures in this section to prehash content on your content servers, add the content to data packages, and then preload the content on your hosted cache servers.

These procedures are optional because you are not required to prehash and preload content on your hosted cache servers.

If you do not preload content, data is added to the hosted cache automatically as clients download it over the WAN connection.

Important

Although these procedures are collectively optional, if you decide to prehash and preload content on your hosted cache servers, performing both procedures is required.

- [Create Content Server Data Packages for Web and File Content (Optional)](8-bc-data-packages)
- [Import Data Packages on the Hosted Cache Server (Optional)](9-bc-import-data)

To continue with this guide, see [Create Content Server Data Packages for Web and File Content (Optional)](8-bc-data-packages).