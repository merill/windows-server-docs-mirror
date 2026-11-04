---
layout: Conceptual
title: Install and Configure Content Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/install-and-configure-content-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to install and configure content servers.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 44264ae5-40a0-191b-6387-8bacf13fda9b
document_version_independent_id: 06ee3c1a-c2b0-adc2-b0c9-8ef347dca6e5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Install-and-Configure-Content-Servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/install-and-configure-content-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Install-and-Configure-Content-Servers.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 957f45a6-2b3c-fc27-1446-e76a8308f4df
---

# Install and Configure Content Servers | Microsoft Learn

When you deploy BranchCache in distributed cache mode or hosted cache mode, you must deploy one or more content servers at your main office or in the cloud. Content servers that are Web servers or application servers use the BranchCache feature. Content servers that are file servers use the BranchCache for network files role service of the File Services server role in Windows Server 2016.

See the following topics to deploy content servers.

- [Install Content Servers that Use the BranchCache Feature](install-content-servers-that-use-the-branchcache-feature)
- [Install File Services Content Servers](install-file-services-content-servers)