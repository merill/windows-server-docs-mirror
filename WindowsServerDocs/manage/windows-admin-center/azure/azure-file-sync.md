---
layout: Conceptual
title: Sync your file server with the cloud by using Azure File Sync | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/azure/azure-file-sync
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Use Azure File Sync to centralize your organization's file shares in Azure, while keeping the flexibility, performance, and compatibility of an on-premises file server. Azure File Sync transforms Windows Server into a quick cache of your Azure file share with the optional cloud tiering feature.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2019-04-12T00:00:00.0000000Z
locale: en-us
document_id: 0c9b4e30-c4e3-acab-2c21-f3f8c74ae7d7
document_version_independent_id: 4d9ae32e-07d1-c721-6bdf-c17357ef3361
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/azure/azure-file-sync.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/azure/azure-file-sync
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/azure/azure-file-sync.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/01a89bec-e73f-4ce0-a00a-ae34ad62e5fe
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50038ab9-5431-4515-9dfc-c24291ef4fce
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: 29dbc196-dfa8-6ee9-7109-305b01adf738
---

# Sync your file server with the cloud by using Azure File Sync | Microsoft Learn

Use Azure File Sync to centralize your organization's file shares in Azure, while keeping the flexibility, performance, and compatibility of an on-premises file server. Azure File Sync transforms Windows Server into a quick cache of your Azure file share with the optional cloud tiering feature. You can use any protocol that's available on Windows Server to access your data locally, including SMB, NFS, and FTPS.

Once your files have synced to the cloud, you can connect multiple servers to the same Azure file share to sync and cache the content locally—permissions (ACLs) are always transported as well. Azure Files offers a snapshot capability that can generate differential snapshots of your Azure file share. These snapshots can even be mounted as read-only network drives via SMB for easy browsing and restore. Combined with cloud tiering, running an on-premises file server has never been easier.

Azure File Sync in Windows Admin Center is supported on Windows Server 2012 R2, Windows Server 2016, Windows Server 2019, Windows Server 2022, and Windows Server 2025.

For more info, see [Planning for an Azure File Sync deployment](/en-us/azure/storage/files/storage-sync-files-planning).