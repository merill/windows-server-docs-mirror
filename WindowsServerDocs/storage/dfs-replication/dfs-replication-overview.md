---
layout: Conceptual
title: Distributed File System (DFS) Replication | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-replication/dfs-replication-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how Distributed File System (DFS) Replication in Windows Server synchronizes folders across multiple servers and sites.
ms.topic: overview
ai-usage: ai-assisted
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-28T00:00:00.0000000Z
locale: en-us
document_id: b52bf5d5-4f44-77aa-e0cb-6e3c331c2ef0
document_version_independent_id: 1ffabaa9-a52f-3abe-7f9c-0e3531e1869f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-replication/dfs-replication-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-replication/dfs-replication-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-replication/dfs-replication-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/01a89bec-e73f-4ce0-a00a-ae34ad62e5fe
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/50038ab9-5431-4515-9dfc-c24291ef4fce
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 48ee98b4-c5e9-6ec0-be88-7649b1681211
---

# Distributed File System (DFS) Replication | Microsoft Learn

Distributed File System (DFS) Replication is a Windows Server role service that lets you efficiently synchronize folders across multiple servers and sites. This article explains how DFS Replication works, its benefits, and how to get started.

DFS Replication is an efficient, active-active replication engine that you can use to keep folders synchronized between servers across limited bandwidth network connections. You can replicate all types of folders, including folders referred to by a [DFS namespace](../dfs-namespaces/dfs-overview) path. The service replaces the File Replication Service (FRS) as the replication engine for DFS namespaces.

Tip

Consider using [Azure File Sync](/en-us/azure/storage/file-sync/file-sync-introduction) to reduce your on-premises storage footprint. Azure File Sync can keep multiple Windows file servers in sync. Each server needs to only keep a cache on-premises while the full copy of the data is in the cloud. Azure File Sync also provides the benefit of cloud backups with integrated snapshots. For more information, see [Planning for an Azure File Sync deployment](/en-us/azure/storage/file-sync/file-sync-planning).

DFS Replication uses a compression algorithm known as *remote differential compression* (RDC). RDC detects changes to the data in a file and enables DFS Replication to replicate only the changed file blocks instead of the entire file.

Active Directory Domain Services (AD DS) uses DFS Replication to replicate the `sysvol` folder in domains that use the Windows Server 2008 or later domain functional level. For more information about replicating the `sysvol` folder by using DFS Replication, see [Migrate the sysvol folder replication to DFS Replication](migrate-sysvol-to-dfsr).

## Understand replication groups

To use DFS Replication, you create *replication groups* and add replicated folders to the groups. Replicated folders are stored on servers in the group, which are referred to as *members*. DFS Replication establishes connections between the members of a group.

The following figure illustrates the relationship between a replication group, the members in the group, and the replicated folders.

![A diagram of a DFS Replication group showing two members with replicated folders and their connection.](media/dfsr-overview.gif)

A *replicated folder* stays synchronized on each member in a group. In the figure, there are two replicated folders: **Projects** and **Proposals**. As the data changes in each replicated folder, the changes are replicated across connections between the members of the replication group. The connections between all members form the replication topology.

Creating multiple replicated folders in a single replication group simplifies the process of deploying replicated folders. The topology, schedule, and bandwidth throttling for the replication group are applied to each replicated folder. Each replicated folder has unique settings, such as file and subfolder filters. The settings let you filter out different files and subfolders for each replicated folder.

The replicated folders stored on each member can be located on different volumes in the member, and the replicated folders don't need to be shared folders or part of a namespace.

## Deploy and manage DFS Replication

DFS Replication is a part of the **File and Storage Services** role for Windows Server. You can install DFS Replication by using Windows Admin Center, Server Manager, or PowerShell. For detailed steps, see [Install DFS Replication](install-dfs-replication).

The management tools for DFS are the DFS Management snap-in, the [DFS Replication PowerShell module](/en-us/powershell/module/dfsr/), and the `dfsradmin` and `dfsrdiag` Windows Commands. These tools need to be installed separately and are available as part of the Remote Server Administration Tools (RSAT). The **DFS Management** snap-in simplifies sharing replicated folders and optionally publishing them in an existing namespace.

### Interoperability with Azure virtual machines

DFS Replication on an Azure virtual machine is a verified scenario for Windows Server. However, there are some limitations and requirements for this implementation.

- **Snapshots and saved states**: to restore a server that's running DFS Replication, don't use snapshots or saved states to replicate anything other than the `sysvol` folder. If you attempt this type of restore, DFS Replication fails. This restoration requires special database recovery steps. Also, don't export, clone, or copy the virtual machines. For more information, see [DFSR no longer replicates files after restoring a virtualized server's snapshot](/en-us/support/windows-server/networking/distributed-file-system-replication-not-replicate-files) and [Safely virtualizing DFSR](https://techcommunity.microsoft.com/t5/storage-at-microsoft/safely-virtualizing-dfsr/ba-p/424671).
- **DFS Replication backups**: to back up data in a replicated folder stored in a virtual machine, use backup software located on the guest virtual machine. Don't back up or restore a virtualized DFS Replication server from the host virtual machine.
- **Domain controller access**: DFS Replication requires access to physical or virtual domain controllers. The DFS Replication service can't communicate directly with Microsoft Entra ID.
- **VPN connection**: DFS Replication requires a VPN connection between your on-premises replication group members and any members hosted in Azure virtual machines. You also need to configure the on-premises router (such as Forefront Threat Management Gateway) to allow the RPC Endpoint Mapper (port 135) and a randomly assigned port between 49152 and 65535 to pass over the VPN connection. You can use the `Set-DfsrMachineConfiguration` cmdlet or the `dfsrdiag` Windows Command to specify a static port instead of the random port. For more information about how to specify a static port for DFS Replication, see [`Set-DfsrServiceConfiguration`](/en-us/powershell/module/dfsr/set-dfsrserviceconfiguration). For information about related ports to open for managing Windows Server, see [Service overview and network port requirements for Windows](/en-us/support/windows-server/networking/service-overview-and-network-port-requirements).

To learn how to get started with Azure virtual machines, visit the [Microsoft Azure website](/en-us/azure/virtual-machines/).