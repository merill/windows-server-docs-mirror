---
layout: Conceptual
title: What is SMB File Sharing for Windows and Windows Server? | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/file-server/file-server-smb-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how the SMB protocol enhances file sharing in Windows Server with features like encryption, performance optimization, and high availability.
ms.topic: overview
author: robinharwood
ms.author: roharwoo
ms.date: 2025-11-27T00:00:00.0000000Z
ai-usage: ai-assisted
ms.custom: os_security, network_security
locale: en-us
document_id: dca900b3-d060-8342-c545-a610d23157ef
document_version_independent_id: ab1fc94a-0c56-8fc7-9875-4cc119438512
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/file-server/file-server-smb-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/file-server/file-server-smb-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/file-server/file-server-smb-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: d018650c-b087-55fa-ba4f-62364d42b9c3
---

# What is SMB File Sharing for Windows and Windows Server? | Microsoft Learn

This article provides an overview of the Server Message Block (SMB) protocol in Windows. It covers practical applications, features, and key concepts for file sharing.

The SMB protocol is a network file sharing protocol. SMB allows you to read and write to files over the network on top of TCP/IP or other protocols. With SMB, an application (or the user of an application) can access files or other resources at a remote server, allowing applications to read, create, and update files on the remote server. SMB can also communicate with any server program that is set up to receive an SMB client request.

SMB is also a fabric protocol for hyperconverged and clustered storage solutions such as Storage Spaces Direct and Storage Replica. For more information, see SMB as a foundation for Windows Server services.

## Usage

This section discusses some practical ways to use the SMB protocol.

- **File storage for virtualization (Hyper-V™ over SMB)**. Hyper-V can store virtual machine files, such as configuration, Virtual hard disk (VHD) files, and snapshots, in file shares over the SMB 3.0 protocol. You can use this feature for both stand-alone file servers and clustered file servers that use Hyper-V together with shared file storage for the cluster.
- **Microsoft SQL Server over SMB**. SQL Server can store user database files on SMB file shares. Currently, SQL Server over SMB is supported with SQL Server 2008 R2 for stand-alone SQL servers. Upcoming versions of SQL Server add support for clustered SQL servers and system databases.
- **Traditional storage for end-user data**. The SMB 3.0 protocol provides enhancements to the Information Worker (or client) workloads. These enhancements include reducing the application latencies experienced by branch office users when accessing data over wide area networks (WAN) and protecting data from eavesdropping attacks.

Note

If you need to conserve storage space on an SMB file share, consider using Azure File Sync with cloud tiering enabled. Azure File Sync allows you to cache your most frequently accessed files locally and tier your least frequently accessed files to the cloud, saving local storage space while maintaining performance. For details, see [Planning for an Azure File Sync deployment](/en-us/azure/storage/files/storage-sync-files-planning).

## SMB features

SMB includes a wide range of features organized into the following categories:

- **Security and authentication** - SMB provides multiple layers of protection including encryption, signing, NTLM blocking, and authentication rate limiting. These features protect data in transit and help prevent unauthorized access and brute-force attacks.
- **Networking and connectivity** - SMB supports multiple transport options including traditional TCP, QUIC for secure internet access without VPN, and RDMA for high-performance datacenter workloads. Features like alternative ports and firewall hardening provide other flexibility and security.
- **Performance** - SMB includes features to optimize file transfer speeds and reduce network overhead, including compression, bandwidth limits, directory caching, and WAN optimizations.
- **High availability and scale** - For enterprise environments, SMB supports transparent failover, scale-out file servers, and rolling cluster upgrades to ensure continuous access to file shares during maintenance or failures.
- **Management and monitoring** - Administrators can manage SMB using PowerShell cmdlets, control dialect versions, and monitor performance through dedicated counters.

For detailed information about individual features and their availability across Windows versions, see [SMB features in Windows and Windows Server](smb-feature-descriptions).

## SMB components

SMB communication involves two components: the SMB client and the SMB server. These terms refer to the SMB protocol roles, not the Windows operating system editions.

- **SMB server** is the component that shares resources (files, printers, named pipes) and responds to requests from SMB clients. When you create a file share on a computer, that computer's SMB server handles incoming connections and file access requests.
- **SMB client** is the component that connects to remote shares and sends requests to SMB servers. When you map a network drive or access a UNC path like `\\server\share`, your computer's SMB client initiates and manages that connection.

Both Windows Server and Windows client operating systems include the SMB client and SMB server components. Meaning a Windows client computer, such as Windows 11, can host file shares (acting as an SMB server) while also connecting to shares on other computers (acting as an SMB client). Similarly, Windows Server can connect to shares hosted on other servers or client computers.

Feature availability varies between operating system versions. Some features are available only in the SMB server component, some only in the SMB client component, and some in both. Additionally, certain features might be available in Windows Server but not in Windows client editions, or vice versa. For more information about feature availability across different Windows versions, see [SMB features in Windows and Windows Server](smb-feature-descriptions).

## SMB dialects

An SMB dialect is a specific version of the SMB protocol that defines the features, capabilities, and message formats supported during communication between a client and server. When you establish an SMB connection, the client and server negotiate to use the highest dialect version that both support. Higher dialect versions provide more features such as improved security, better performance, and new capabilities, while maintaining backward compatibility with older versions.

The following table shows which SMB dialect version is supported by each Windows operating system release.

| SMB Dialect | Windows Client | Windows Server |
| --- | --- | --- |
| SMB 3.1.1 | Windows 10 version 1607 and later | Windows Server 2016 and later |
| SMB 3.02 | Windows 8.1 | Windows Server 2012 R2 |
| SMB 3.0 | Windows 8 | Windows Server 2012 |

Note

While multiple Windows versions support the same SMB dialect (3.1.1), each version introduces more features and enhancements beyond the base protocol. For more information about version-specific improvements and feature availability, see [SMB features in Windows and Windows Server](smb-feature-descriptions).

## SMB as a foundation

SMB serves as the underlying protocol for many Windows Server storage and file services. These services build on SMB to provide more capabilities while inheriting SMB's security, performance, and reliability features.

### Hyperconverged and clustered storage

SMB is a fabric protocol for hyperconverged infrastructure (HCI) and clustered storage solutions:

- **Storage Spaces Direct** uses SMB 3 for node-to-node communication, including data replication and cache synchronization in hyperconverged and disaggregated deployments. SMB Direct (RDMA) provides high-throughput, low-latency connectivity between cluster nodes. For more information, see [Storage Spaces Direct overview](../storage-spaces/storage-spaces-direct-overview).
- **Storage Replica** uses SMB 3 to replicate data between servers or clusters for disaster recovery. SMB encryption protects replicated data in transit. For more information, see [Storage Replica overview](../storage-replica/storage-replica-overview).
- **Disaggregated storage architectures** separate compute and storage into distinct clusters, with compute clusters accessing storage over SMB 3. This architecture enables independent scaling of compute and storage resources. For more information, see [Failover clustering storage architectures](../../failover-clustering/storage-architectures).

### File server technologies

Several file server features rely on SMB for file access:

- **Scale-Out File Server** provides continuously available file shares across multiple cluster nodes using SMB 3. Applications like Hyper-V and SQL Server can store data on these shares with transparent failover. For more information, see [Scale-Out File Server overview](../../failover-clustering/sofs-overview).
- **DFS Namespaces** organizes shared folders across multiple servers into a logical namespace. While DFS Namespaces manages the namespace and referrals, the actual file access uses SMB. For more information, see [DFS Namespaces overview](../dfs-namespaces/dfs-overview).
- **DFS Replication** replicates folders between servers for redundancy and branch office scenarios. The replicated content is accessed through SMB file shares. For more information, see [DFS Replication overview](../dfs-replication/dfsr-overview).

### Virtualization and application workloads

SMB 3 enables high-performance storage for virtualized environments:

- **Hyper-V over SMB** allows you to store virtual machine files (configuration, VHD/VHDX, and checkpoints) on SMB 3 file shares instead of local storage. This feature simplifies storage management and enables features like live migration. For more information, see [Deploy Hyper-V over SMB](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj134187%28v=ws.11%29).
- **SQL Server over SMB** supports storing database files on SMB 3 shares, so you can benefit from SMB Multichannel and SMB Direct for performance.

These services benefit from SMB features like encryption, signing, Multichannel, and Direct (RDMA). When you enable SMB security features, the services that depend on SMB inherit those protections.

## Event logging and auditing

SMB provides event logging and auditing capabilities to help administrators monitor file sharing activity, troubleshoot connectivity issues, and detect potential security threats.

Windows records SMB events in the Windows Event Log under **Applications and Services Logs &gt; Microsoft &gt; Windows &gt; SMBClient** and **SMBServer**. These logs capture connection events, authentication failures, share access, and protocol negotiation details. Administrators can use these logs to diagnose connectivity problems, identify misconfigured clients, or investigate unauthorized access attempts.

Beginning with Windows Server 2025 and Windows 11 24H2, SMB includes enhanced auditing capabilities for signing and encryption. Administrators can audit whether clients and servers support SMB signing and encryption, helping identify noncompliant devices that might pose security risks. You can configure this auditing through Group Policy or PowerShell.

For more information about SMB security auditing, see [SMB security enhancements](smb-security).