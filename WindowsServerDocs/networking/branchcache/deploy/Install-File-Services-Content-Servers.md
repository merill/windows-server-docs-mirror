---
layout: Conceptual
title: Install File Services Content Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/install-file-services-content-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to install the BranchCache for network files role service of the File Services server role and enable BranchCache on file shares according to your requirements.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: a9ca67db-1f66-47c9-ab28-44f9f8c6d8fc
document_version_independent_id: b3df3467-456c-5d5e-fbd4-a6b4a87349fd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/Install-File-Services-Content-Servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/install-file-services-content-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/Install-File-Services-Content-Servers.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 09cc0113-445e-9ed4-4c69-8095539513e3
---

# Install File Services Content Servers | Microsoft Learn

To deploy content servers that are running the File Services server role, you must install the BranchCache for network files role service of the File Services server role. In addition, you must enable BranchCache on file shares according to your requirements.

During the configuration of the content server, you can allow BranchCache publication of content for all file shares or you can select a subset of file shares to publish.

Note

When you deploy a BranchCache enabled file server or Web server as a content server, content information is now calculated offline, well before a BranchCache client requests a file. Because of this improvement, you do not need to configure hash publication for content servers, as you did in the previous version of BranchCache.

This automatic hash generation provides faster performance and more bandwidth savings, because content information is ready for the first client that requests the content, and calculations have already been performed.

See the following topics to deploy content servers.

- [Configure the File Services server role](configure-the-file-services-server-role)
- [Enable Hash Publication for File Servers](enable-hash-publication-for-file-servers)
- [Enable BranchCache on a File Share (Optional)](enable-bc-on-file-share)