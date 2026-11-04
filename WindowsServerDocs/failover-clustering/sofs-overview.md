---
layout: Conceptual
title: Scale-Out File Server for application data overview for Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/failover-clustering/sofs-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: failover-clustering
ms.update-cycle: 1095-days
description: How to plan for and deploy a Scale-Out File Server. This allows sharing the same folder from multiple nodes of the same cluster for file-based server application storage availability.
ms.topic: overview
author: robinharwood
ms.author: roharwoo
ms.date: 2025-02-06T00:00:00.0000000Z
locale: en-us
document_id: 07d7bf3d-4ab7-3f11-acb2-840d86090042
document_version_independent_id: ba1dc68b-297a-3c2f-2e99-4f42367e89f7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/failover-clustering/sofs-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: failover-clustering/sofs-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/failover-clustering/sofs-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 929b1224-ee77-4880-1721-605f7b51afaa
---

# Scale-Out File Server for application data overview for Windows Server | Microsoft Learn

Scale-Out File Server is designed to provide scale-out file shares that are continuously available for file-based server application storage. Scale-out file shares allow you to share the same folder from multiple nodes of the same cluster. This scenario focuses on how to plan for and deploy Scale-Out File Server.

You can deploy and configure a clustered file server by using either of the following methods:

- **Scale-Out File Server for application data**: This clustered file server feature was introduced in Windows Server 2012. It lets you store server application data, such as Hyper-V virtual machine files on file shares, and obtain a similar level of reliability, availability, manageability, and high performance that you would expect from a storage area network. All file shares are simultaneously online on all nodes. File shares associated with this type of clustered file server are called scale-out file shares. This is sometimes referred to as active-active. This is the recommended file server type when deploying either Hyper-V over Server Message Block (SMB) or Microsoft SQL Server over SMB.
- **File Server for general use**: This is the continuation of the clustered file server that's supported in Windows Server since the introduction of Failover Clustering. This type of clustered file server, and therefore all the shares associated with the clustered file server, is online on one node at a time. This is sometimes referred to as active-passive or dual-active. File shares associated with this type of clustered file server are called clustered file shares. This is the recommended file server type when deploying information worker scenarios.

## Scenario description

With scale-out file shares, you can share the same folder from multiple nodes of a cluster. If you have a four-node file server cluster that is using SMB Scale-Out, including a device running Windows Server 2012 R2 (or Windows Server 2012), you can access file shares from any of the four nodes. This is achieved by applying new Windows Server Failover Clustering features and the capabilities of the Windows file server protocol, SMB 3.0. File server administrators can provide scale-out file shares and continuously available file services to server applications and respond to increased demands quickly by bringing more servers online. All of this can be done in a production environment, and it's transparent to the server application.

Key benefits provided by Scale-Out File Server include:

- **Active-Active file shares**: All cluster nodes can accept and serve SMB client requests. By making the file share content accessible through all cluster nodes simultaneously, SMB 3.0 clusters and clients cooperate to provide transparent failover to alternative cluster nodes during planned maintenance and unplanned failures with service interruption.
- **Increased bandwidth**: The maximum share bandwidth is the total bandwidth of all file server cluster nodes. Unlike previous versions of Windows Server, the total bandwidth is no longer constrained to the bandwidth of a single cluster node; but rather, the capability of the backing storage system defines the constraints. You can increase the total bandwidth by adding nodes.
- **CHKDSK with zero downtime**: CHKDSK in Windows Server 2012 is enhanced to dramatically shorten the time a file system is offline for repair. Clustered shared volumes (CSVs) take this one step further by eliminating the offline phase. A CSV File System (CSVFS) can use CHKDSK without impacting applications with open handles on the file system.
- **Clustered Shared Volume cache**: CSVs in Windows Server 2012 introduces support for a Read cache, which can significantly improve performance in certain scenarios, such as in Virtual Desktop Infrastructure (VDI).
- **Simpler management**: With Scale-Out File Server, you create the scale-out file servers, and then add the necessary CSVs and file shares. It's no longer necessary to create multiple clustered file servers, each with separate cluster disks, and then develop placement policies to ensure activity on each cluster node.
- **Automatic rebalancing of Scale-Out File Server clients**: In Windows Server 2012 R2, automatic rebalancing improves scalability and manageability for scale-out file servers. SMB client connections are tracked per file share (instead of per server), and clients are redirected to the cluster node with the best access to the volume used by the file share. This improves efficiency by reducing redirection traffic between file server nodes. Clients are redirected following an initial connection and when cluster storage is reconfigured.

## In this scenario

The following articles are available to help you deploy a Scale-Out File Server:

- [Plan for Scale-Out File Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj134258%28v%3dws.11%29)

    - [Step 1: Plan for Storage in Scale-Out File Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj134181%28v%3dws.11%29)
    - [Step 2: Plan for Networking in Scale-Out File Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj134253%28v%3dws.11%29)
- [Deploy Scale-Out File Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831359%28v%3dws.11%29)

    - [Step 1: Install Prerequisites for Scale-Out File Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831478%28v%3dws.11%29)
    - [Step 2: Configure Scale-Out File Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831718%28v%3dws.11%29)
    - [Step 3: Configure Hyper-V to Use Scale-Out File Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831463%28v%3dws.11%29)
    - [Step 4: Configure Microsoft SQL Server to Use Scale-Out File Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831815%28v%3dws.11%29)

## When to use Scale-Out File Server

You shouldn't use Scale-Out File Server if your workload generates a high number of metadata operations, such as opening files, closing files, creating new files, or renaming existing files. A typical information worker would generate several metadata operations. You should use a Scale-Out File Server if you need scalability and simplicity, and if your requirements align with the technologies supported by Scale-Out File Server.

The following table lists the capabilities in SMB 3.0, the common Windows file systems, file server data management technologies, and common workloads. You can see whether the technology is supported with Scale-Out File Server, or if it requires a traditional clustered file server (also known as a file server for general use).

| Technology area | Feature | General use File Server Cluster | Scale-Out File Server |
| --- | --- | --- | --- |
| Applications | Hyper-V | Not recommended | Yes |
| Applications | Microsoft SQL Server | Not recommended | Yes |
| File Management | BranchCache | Yes | No |
| File Management | Data Deduplication (Windows Server 2012) | Yes | No |
| File Management | Data Deduplication (Windows Server 2012 R2) | Yes | Yes (VDI only) |
| File Management | DFS Namespace (DFSN) folder target server | Yes | Yes |
| File Management | DFS Namespace (DFSN) root server root | Yes | No |
| File Management | DFS Replication (DFSR) | Yes | No |
| File Management | Dynamic Access Control (claim-based access, CAP) | Yes | No |
| File Management | File Classification Infrastructure | Yes | No |
| File Management | File Server Resource Manager (Screens and Quotas) | Yes | No |
| File Management | Folder Redirection | Yes | Not recommended |
| File Management | Home Directories | Yes | Not recommended |
| File Management | Offline Files (client side caching) | Yes | Not recommended |
| File Management | Roaming User Profiles | Yes | Not recommended |
| File Management | Work Folders | Yes | No |
| File System | Cluster Shared Volume File System (CSV) | NA | Yes |
| File System | NTFS | Yes | NA |
| File System | Resilient File System (ReFS) | Recommended with Storage Spaces Direct | Recommended with Storage Spaces Direct |
| NFS | NFS Server | Yes | No |
| SMB | SMB Continuous Availability^1^ | Yes | Yes |

^1^SMB loopback Continuous Availability (CA) in hyper-converged configurations is available in Windows Server 2019. To learn more, see [Deploy a cluster set](/en-us/windows-server/storage/storage-spaces/cluster-sets#scale-out-file-server-and-cluster-sets).

Note

The following generate numerous write operations that must be immediately committed to disk (without buffering) when using continuously available file shares. This requirement can reduce performance compared to general-purpose file shares:

- Folder Redirection
- Offline Files
- Roaming User Profiles
- Home Directories

Continuously available file shares are also incompatible with File Server Resource Manager and PCs running Windows XP. Offline Files might not transition to offline mode for 3-6 minutes after a user loses access to a share.

## Practical applications

Scale-Out File Servers are ideal for server application storage. Some examples of server applications that can store their data on a scale-out file share and are as follows:

- The Internet Information Services (IIS) Web server can store configuration and data for Web sites on a scale-out file share. For more information, see [Shared Configuration](https://www.iis.net/learn/manage/managing-your-configuration-settings/shared-configuration_264).
- Hyper-V can store configuration and live virtual disks on a scale-out file share. For more information, see [Deploy Hyper-V over SMB](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj134187%28v%3dws.11%29).
- SQL Server can store live database files on a scale-out file share. For more information, see [Install SQL Server with SMB file share as a storage option](/en-us/sql/database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option).
- Virtual Machine Manager (VMM) can store a library share (which contains virtual machine templates and related files) on a scale-out file share. However, the library server itself can't be a Scale-Out File Server—it must be on a stand-alone server or a failover cluster that doesn't use the Scale-Out File Server cluster role.

If you use a scale-out file share as a library share, you can use only technologies that are compatible with Scale-Out File Server. For example, you can't use Distributed File System (DFS) Replication to replicate a library share hosted on a scale-out file share. It's also important that the scale-out file server has the latest software updates installed.

To use a scale-out file share as a library share, first add a library server (likely a virtual machine) with a local share or no shares at all. Then when you add a library share, choose a file share that's hosted on a scale-out file server. Virtual Machine Manager (VMM) should manage this share and create it exclusively for the library server's use.

Also make sure to install the latest updates on the scale-out file server. For more information about adding VMM library servers and library shares, see [Add profiles to the VMM library](/en-us/system-center/vmm/library-profiles). For a list of currently available hotfixes for File and Storage Services, see [Microsoft Knowledge Base article 2899011](https://support.microsoft.com/help/2899011/).

Note

Some users, such as information workers, have workloads that have a greater impact on performance. For example, operations like opening and closing files, creating new files, and renaming existing files, when performed by multiple users, have an impact on performance. If a file share is enabled with continuous availability, it provides data integrity, but it also affects the overall performance. Continuous availability requires that data writes through to the disk to ensure integrity if a failure of a cluster node in a Scale-Out File Server were to occur. Therefore, a user that copies several large files to a file server can expect slower performance on continuously available file share.

## Features included in this scenario

The following table lists the features that are part of this scenario and describes how they support it.

| Feature | How this scenario is supported |
| --- | --- |
| [Failover Clustering](/en-us/windows-server/failover-clustering/failover-clustering-overview) | Failover clusters added the following features in Windows Server 2012 to support scale-Out file server: Distributed Network Name, the Scale-Out File Server resource type, Cluster Shared Volumes (CSV) 2, and the Scale-Out File Server High Availability role. For more information about these features, see [What's New in Failover Clustering in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn265972%28v%3dws.11%29). |
| [Server Message Block](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831795%28v%3dws.11%29) | SMB 3.0 added the following features in Windows Server to support Scale-Out File Server, SMB Transparent Failover, SMB Multichannel, and SMB Direct. For more information on new and changed functionality for SMB, see [Overview of file sharing using the SMB 3 protocol in Windows Server](/en-us/windows-server/storage/file-server/file-server-smb-overview). |