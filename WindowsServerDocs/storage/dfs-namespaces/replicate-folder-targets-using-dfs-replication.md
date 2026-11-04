---
layout: Conceptual
title: Replicate Folder Targets using DFS Replication | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/replicate-folder-targets-using-dfs-replication
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to replicate folder targets using DFS Replication
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 3ca7c6e4-0681-f444-54e3-b1c85cefa474
document_version_independent_id: 93df9f2a-c4e2-0e92-b6eb-c8cefe61c641
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/replicate-folder-targets-using-dfs-replication.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/replicate-folder-targets-using-dfs-replication
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/replicate-folder-targets-using-dfs-replication.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 9cc8bfcf-5be6-7a34-ac86-f7e4bf2139d4
---

# Replicate Folder Targets using DFS Replication | Microsoft Learn

You can use DFS Replication to keep the contents of folder targets in sync so that users see the same files regardless of which folder target the client computer is referred to.

## To replicate folder targets using DFS Replication

1. Click **Start**, point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, right-click a folder that has two or more folder targets, and then click **Replicate Folder**.
3. Follow the instructions in the Replicate Folder Wizard.

Note

Configuration changes are not applied immediately to all members except when using the [Suspend-DfsReplicationGroup](/en-us/powershell/module/dfsr/suspend-dfsreplicationgroup) and [Sync-DfsReplicationGroup](/en-us/powershell/module/dfsr/sync-dfsreplicationgroup) cmdlets. The new configuration must be replicated to all domain controllers, and each member in the replication group must poll its closest domain controller to obtain the changes. The amount of time this takes depends on the Active Directory Directory Services (AD DS) replication latency and the long polling interval (60 minutes) on each member. To poll immediately for configuration changes, open a Command Prompt window and then type the following command once for each member of the replication group:  dfsrdiag.exe PollAD /Member:DOMAIN\Server1  To do so from a Windows PowerShell session, use the [Update-DfsrConfigurationFromAD](/en-us/powershell/module/dfsr/update-dfsrconfigurationfromad) cmdlet, which was introduced in Windows Server 2012 R2.

## Additional References

- [Deploying DFS Namespaces](deploying-dfs-namespaces)
- [Delegate Management Permissions for DFS Namespaces](delegate-management-permissions-for-dfs-namespaces)
- [DFS Replication](../dfs-replication/dfs-replication-overview)