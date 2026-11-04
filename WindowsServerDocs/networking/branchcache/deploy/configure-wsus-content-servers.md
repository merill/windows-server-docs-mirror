---
layout: Conceptual
title: Configure Windows Server Update Services (WSUS) Content Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/deploy/configure-wsus-content-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to configure Windows Server Update Services (WSUS) Content Servers to store update files on the local computer.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: 19564a2c-2d66-4df0-9913-7ebb082c96b3
document_version_independent_id: b843917d-8985-e15c-d67d-0392c592549d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/deploy/configure-wsus-content-servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/deploy/configure-wsus-content-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/deploy/configure-wsus-content-servers.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 81caecac-1cb7-34b8-fc8e-48dee3283a44
---

# Configure Windows Server Update Services (WSUS) Content Servers | Microsoft Learn

After installing the BranchCache feature and starting the BranchCache service, WSUS servers must be configured to store update files on the local computer.

When you configure WSUS servers to store update files on the local computer, both the update metadata and the update files are downloaded by and stored directly upon the WSUS server. This ensures that BranchCache client computers receive Microsoft product update files from the WSUS server rather than directly from the Microsoft Update Web site.

For more information about WSUS synchronization, see [Setting up Update Synchronizations](../../../administration/windows-server-update-services/manage/setting-up-update-synchronizations)