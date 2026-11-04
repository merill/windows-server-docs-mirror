---
layout: Conceptual
title: Comparison of Windows Server editions | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/editions-comparison
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: 'Learn about the differences between Windows Server Standard, Datacenter, Datacenter: Azure Edition and Annual Channel for Containers editions.'
ms.topic: product-comparison
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-01T00:00:00.0000000Z
zone_pivot_groups: windows-os-version
locale: en-us
document_id: 5667111c-6198-d8ee-a0e4-b8040aa1ef8c
document_version_independent_id: 5667111c-6198-d8ee-a0e4-b8040aa1ef8c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/editions-comparison.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/editions-comparison
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/editions-comparison.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: ddd53142-e9f9-8e4c-3027-4a11c0eb38c6
---

# Comparison of Windows Server editions | Microsoft Learn

Use this article to compare the Standard, Datacenter, and Datacenter: Azure Edition of Windows Server to see which is most appropriate for you.

Tip

If you're looking for information about the locks and limits in Windows Server, see [Comparison of locks and limits in Windows Server](locks-limits).

## Available roles and features

::: zone pivot="windows-server-2025"

| Feature | Subfeature | Standard edition | Datacenter edition | Datacenter: Azure Edition |
| --- | --- | --- | --- | --- |
| .NET Framework 3.5 Features |  | ✅ | ✅ | ✅ |
| .NET Framework 4.8 Features |  | ✅ | ✅ | ✅ |
| Activation |  | ✅ | ✅ | ✅ |
|  | Automatic Virtual Machine Activation | ⚠️¹ | ✅ | ✅² |
|  | Key Management Service (KMS) | ✅ | ✅ | ❌³ |
| Active Directory Certificate Services |  | ✅ | ✅ | ✅ |
|  | Certificate Enrollment Policy Web Service | ✅ | ✅ | ✅ |
|  | Certificate Enrollment Web Service | ✅ | ✅ | ✅ |
|  | Certification Authority | ✅ | ✅ | ✅ |
|  | Certification Authority Web Enrollment | ✅ | ✅ | ✅ |
|  | Network Device Enrollment Service | ✅ | ✅ | ✅ |
|  | Online Responder | ✅ | ✅ | ✅ |
| Active Directory Domain Services |  | ✅ | ✅ | ✅ |
| Active Directory Federation Services |  | ✅ | ✅ | ✅ |
| Active Directory Lightweight Directory Services |  | ✅ | ✅ | ✅ |
| Active Directory Rights Management Services |  | ✅ | ✅ | ✅ |
| Azure Extended Networking |  | ❌ | ❌ | ✅ |
| Background Intelligent Transfer Service (BITS) |  | ✅ | ✅ | ✅ |
| BitLocker Drive Encryption |  | ✅ | ✅ | ✅ |
| BitLocker Network Unlock |  | ✅⁴ | ✅⁴ | ✅⁴ |
| BranchCache |  | ✅ | ✅ | ✅ |
| Client for NFS |  | ✅ | ✅ | ✅ |
| Data Center Bridging |  | ✅ | ✅ | ✅ |
| Device Health Attestation |  | ✅ | ✅ | ✅ |
| DHCP Server |  | ✅ | ✅ | ✅ |
| Direct Play |  | ✅⁴ | ✅⁴ | ✅⁴ |
| DLNA codecs and web media streaming |  | ✅⁴ | ✅⁴ | ✅⁴ |
| DNS Server |  | ✅ | ✅ | ✅ |
| Enhanced Storage |  | ✅ | ✅ | ✅ |
| Failover Clustering |  | ✅ | ✅ | ✅ |
| Fax Server |  | ✅ | ✅ | ✅ |
| File and Storage Services |  | ✅ | ✅ | ✅ |
|  | BranchCache for Network Files | ✅ | ✅ | ✅ |
|  | Data Deduplication | ✅ | ✅ | ✅ |
|  | DFS Namespaces | ✅ | ✅ | ✅ |
|  | DFS Replication | ✅ | ✅ | ✅ |
|  | File Server | ✅ | ✅ | ✅ |
|  | File Server Resource Manager | ✅ | ✅ | ✅ |
|  | File Server VSS Agent Service | ✅ | ✅ | ✅ |
|  | iSCSI Target Server | ✅ | ✅ | ✅ |
|  | iSCSI Target Storage Provider (VDS and VSS hardware providers) | ✅ | ✅ | ✅ |
|  | Server for NFS | ✅ | ✅ | ✅ |
|  | SMB 1.0/CIFS File Sharing Support | ✅ | ✅ | ✅ |
|  | SMB Bandwidth Limit | ✅ | ✅ | ✅ |
|  | SMB over QUIC | ✅ | ✅ | ✅ |
|  | Work Folders | ✅ | ✅ | ✅ |
|  | Storage Migration Service | ✅ | ✅ | ✅ |
|  | Storage Migration Service Proxy | ✅ | ✅ | ✅ |
|  | Storage Spaces | ✅ | ✅ | ✅ |
|  | Storage Spaces Direct | ❌ | ✅ | ✅ |
|  | Storage Replica | ✅ | ✅ | ✅ |
| Group Policy Management |  | ✅ | ✅ | ✅ |
| Host Guardian Hyper-V Support |  | ❌ | ✅ | ✅ |
| Host Guardian Service |  | ✅ | ✅ | ✅ |
| Hotpatching |  | ✅⁵ | ✅⁵ | ✅ |
| I/O Quality of Service |  | ✅ | ✅ | ✅ |
| IIS Hostable Web Core |  | ✅ | ✅ | ✅ |
| IP Address Management (IPAM) Server |  | ✅ | ✅ | ✅ |
| Management OData IIS Extension |  | ✅ | ✅ | ✅ |
| Media Foundation |  | ✅ | ✅ | ✅ |
| Message Queuing |  | ✅ | ✅ | ✅ |
|  | Message Queuing DCOM Proxy | ✅ | ✅ | ✅ |
|  | Message Queuing Services | ✅ | ✅ | ✅ |
| Microsoft Defender Antivirus |  | ✅ | ✅ | ✅ |
| Multipath I/O |  | ✅ | ✅ | ✅ |
| MultiPoint Connector |  | ✅ | ✅ | ✅ |
| Network ATC |  | ✅ | ✅ | ✅ |
| Network Controller |  | ❌ | ✅ | ✅ |
| Network Load Balancing |  | ✅ | ✅ | ✅ |
| Network Policy and Access Services |  | ✅⁴ | ✅⁴ | ✅⁴ |
| Network Virtualization |  | ✅ | ✅ | ✅ |
| Print and Document Services |  | ✅ | ✅ | ✅ |
|  | Internet Printing | ✅⁴ | ✅⁴ | ✅⁴ |
|  | Line Printer Daemon (LPD) Service | ✅⁴ | ✅⁴ | ✅⁴ |
|  | Print Server | ✅⁴ | ✅⁴ | ✅⁴ |
| Quality Windows Audio Video Experience |  | ✅ | ✅ | ✅ |
| RAS Connection Manager Administration Kit (CMAK) |  | ✅ | ✅ | ✅ |
| Remote Access |  | ✅ | ✅ | ✅ |
|  | DirectAccess and VPN (RAS) | ✅ | ✅ | ✅ |
|  | Routing | ✅ | ✅ | ✅ |
|  | Web Application Proxy | ✅ | ✅ | ✅ |
| Remote Assistance |  | ✅⁴ | ✅⁴ | ✅⁴ |
| Remote Desktop Services |  | ✅⁴ | ✅⁴ | ✅⁴ |
| Remote Differential Compression |  | ✅ | ✅ | ✅ |
| Remote Server Administration Tools |  | ✅ | ✅ | ✅ |
| RPC over HTTP Proxy |  | ✅ | ✅ | ✅ |
| Setup and Boot Event Collection |  | ✅ | ✅ | ✅ |
| Simple TCP/IP Services |  | ✅⁴ | ✅⁴ | ✅⁴ |
| SNMP Service |  | ✅ | ✅ | ✅ |
| Software Load Balancer |  | ✅ | ✅ | ✅ |
| System Data Archiver |  | ✅ | ✅ | ✅ |
| System Insights |  | ✅ | ✅ | ✅ |
| Telnet Client |  | ✅ | ✅ | ✅ |
| TFTP Client |  | ✅⁴ | ✅⁴ | ✅⁴ |
| Virtualization |  | ✅ | ✅ | ✅ |
|  | Containers | ✅ | ✅ | ❌ |
|  | Hyper-V | ✅ | ✅ | ✅ |
|  | GPU partitioning | ✅⁶ | ✅ | ✅⁶ |
|  | VM Shielding Tools for Fabric Management | ✅ | ✅ | ✅ |
| Volume Activation Services |  | ✅ | ✅ | ✅ |
| Web Server (IIS) |  | ✅ | ✅ | ✅ |
|  | FTP Server | ✅ | ✅ | ✅ |
|  | Web Server | ✅ | ✅ | ✅ |
| WebDAV Redirector |  | ✅ | ✅ | ✅ |
| Windows Biometric Framework |  | ✅⁴ | ✅⁴ | ✅⁴ |
| Windows Deployment Services |  | ✅ | ✅ | ✅ |
| Windows Identity Foundation 3.5 |  | ✅⁴ | ✅⁴ | ✅⁴ |
| Windows Internal Database |  | ✅ | ✅ | ✅ |
| Windows PowerShell |  | ✅ | ✅ | ✅ |
|  | Windows PowerShell 2.0 Engine | ✅ | ✅ | ✅ |
|  | Windows PowerShell 5.1 | ✅ | ✅ | ✅ |
|  | Windows PowerShell Desired State Configuration Service | ✅ | ✅ | ✅ |
|  | Windows PowerShell Web Access | ✅ | ✅ | ✅ |
| Windows Process Activation Service |  | ✅ | ✅ | ✅ |
| Windows Server Management enabled by Azure Arc |  | ✅⁷ | ✅⁷ | ✅⁷ |
|  | Azure Update Manager | ✅⁷ | ✅⁷ | ✅⁷ |
|  | Change Tracking and Inventory | ✅⁷ | ✅⁷ | ✅⁷ |
|  | Azure Machine Configuration | ✅⁷ | ✅⁷ | ✅⁷ |
|  | Windows Admin Center in Azure for Arc | ✅⁷ | ✅⁷ | ✅⁷ |
|  | Remote Support | ✅⁷ | ✅⁷ | ✅⁷ |
|  | Network HUD | ✅⁷ | ✅⁷ | ✅⁷ |
|  | Best Practices Assessment | ✅⁷ | ✅⁷ | ✅⁷ |
|  | Azure Site Recovery Configuration | ✅⁷ | ✅⁷ | ✅⁷ |
| Windows Search Service |  | ✅⁴ | ✅⁴ | ✅⁴ |
| Windows Server Backup |  | ✅ | ✅ | ✅ |
| Windows Server Migration Tools |  | ✅ | ✅ | ✅ |
| Windows Server Update Services |  | ✅ | ✅ | ✅ |
| Windows Standards-Based Storage Management |  | ✅ | ✅ | ✅ |
| Windows Subsystem for Linux |  | ✅ | ✅ | ✅ |
| Windows TIFF IFilter |  | ✅⁴ | ✅⁴ | ✅⁴ |
| WinRM IIS Extension |  | ✅ | ✅ | ✅ |
| WINS Server |  | ✅ | ✅ | ✅ |
| Wireless LAN Service |  | ✅ | ✅ | ✅ |
| WoW64 Support |  | ✅ | ✅ | ✅ |
| XPS Viewer |  | ✅⁴ | ✅⁴ | ✅⁴ |

1. As a guest if hosted on a virtualization host activated with Datacenter edition
2. Datacenter: Azure Edition can be used as a nested host or guest
3. Activated by Azure and can't be configured as a KMS host
4. When installed as Server with Desktop Experience
5. Available as an Azure Arc-enabled service. To learn more about Azure Arc pricing, see the [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/)
6. Available with Windows Server 2025 Standard, and is designed for standalone servers. Live migrate VMs between standalone nodes for planned downtime. If clustering is required for unplanned downtime, Windows Server 2025 Datacenter must be used instead.
7. Available for machines enrolled in Windows Server Management enabled by Azure Arc with Windows Server licenses that have active Software Assurances or Windows Server licenses that with active subscription licenses. To learn more about the available Azure benefits, billing, and requirements, see [Windows Server Management enabled by Azure Arc](/en-us/azure/azure-arc/servers/windows-server-management-overview).

::: zone-end

::: zone pivot="windows-server-2022"

| Feature | Subfeature | Standard edition | Datacenter edition | Datacenter: Azure Edition |
| --- | --- | --- | --- | --- |
| .NET Framework 3.5 Features |  | ✅ | ✅ | ✅ |
| .NET Framework 4.8 Features |  | ✅ | ✅ | ✅ |
| Activation |  | ✅ | ✅ | ✅ |
|  | Automatic Virtual Machine Activation | ⚠️¹ | ✅ | ✅ |
|  | Key Management Service (KMS) | ✅ | ✅ | ❌² |
| Active Directory Certificate Services |  | ✅ | ✅ | ✅ |
|  | Certificate Enrollment Policy Web Service | ✅ | ✅ | ✅ |
|  | Certificate Enrollment Web Service | ✅ | ✅ | ✅ |
|  | Certification Authority | ✅ | ✅ | ✅ |
|  | Certification Authority Web Enrollment | ✅ | ✅ | ✅ |
|  | Network Device Enrollment Service | ✅ | ✅ | ✅ |
|  | Online Responder | ✅ | ✅ | ✅ |
| Active Directory Domain Services |  | ✅ | ✅ | ✅ |
| Active Directory Federation Services |  | ✅ | ✅ | ✅ |
| Active Directory Lightweight Directory Services |  | ✅ | ✅ | ✅ |
| Active Directory Rights Management Services |  | ✅ | ✅ | ✅ |
| Background Intelligent Transfer Service (BITS) |  | ✅ | ✅ | ✅ |
| BitLocker Drive Encryption |  | ✅ | ✅ | ✅ |
| BitLocker Network Unlock |  | ✅³ | ✅³ | ✅³ |
| BranchCache |  | ✅ | ✅ | ✅ |
| Client for NFS |  | ✅ | ✅ | ✅ |
| Data Center Bridging |  | ✅ | ✅ | ✅ |
| Device Health Attestation |  | ✅ | ✅ | ✅ |
| DHCP Server |  | ✅ | ✅ | ✅ |
| Direct Play |  | ✅³ | ✅³ | ✅³ |
| DLNA codecs and web media streaming |  | ✅³ | ✅³ | ✅³ |
| DNS Server |  | ✅ | ✅ | ✅ |
| Enhanced Storage |  | ✅ | ✅ | ✅ |
| Failover Clustering |  | ✅ | ✅ | ✅ |
| Fax Server |  | ✅ | ✅ | ✅ |
| File and Storage Services |  | ✅ | ✅ | ✅ |
|  | BranchCache for Network Files | ✅ | ✅ | ✅ |
|  | Data Deduplication | ✅ | ✅ | ✅ |
|  | DFS Namespaces | ✅ | ✅ | ✅ |
|  | DFS Replication | ✅ | ✅ | ✅ |
|  | File Server | ✅ | ✅ | ✅ |
|  | File Server Resource Manager | ✅ | ✅ | ✅ |
|  | File Server VSS Agent Service | ✅ | ✅ | ✅ |
|  | iSCSI Target Server | ✅ | ✅ | ✅ |
|  | iSCSI Target Storage Provider (VDS and VSS hardware providers) | ✅ | ✅ | ✅ |
|  | Server for NFS | ✅ | ✅ | ✅ |
|  | SMB 1.0/CIFS File Sharing Support | ✅ | ✅ | ✅ |
|  | SMB Bandwidth Limit | ✅ | ✅ | ✅ |
|  | SMB over QUIC | ❌ | ❌ | ✅ |
|  | Work Folders | ✅ | ✅ | ✅ |
|  | Storage Migration Service | ✅ | ✅ | ✅ |
|  | Storage Migration Service Proxy | ✅ | ✅ | ✅ |
|  | Storage Spaces | ✅ | ✅ | ✅ |
|  | Storage Spaces Direct | ❌ | ✅ | ✅ |
|  | Storage Replica | ✅ | ✅ | ✅ |
| Group Policy Management |  | ✅ | ✅ | ✅ |
| Host Guardian Hyper-V Support |  | ❌ | ✅ | ✅ |
| Host Guardian Service |  | ✅ | ✅ | ✅ |
| Hotpatching |  | ❌ | ❌ | ✅ |
| I/O Quality of Service |  | ✅ | ✅ | ✅ |
| IIS Hostable Web Core |  | ✅ | ✅ | ✅ |
| IP Address Management (IPAM) Server |  | ✅ | ✅ | ✅ |
| Management OData IIS Extension |  | ✅ | ✅ | ✅ |
| Media Foundation |  | ✅ | ✅ | ✅ |
| Message Queuing |  | ✅ | ✅ | ✅ |
|  | Message Queuing DCOM Proxy | ✅ | ✅ | ✅ |
|  | Message Queuing Services | ✅ | ✅ | ✅ |
| Microsoft Defender Antivirus |  | ✅ | ✅ | ✅ |
| Multipath I/O |  | ✅ | ✅ | ✅ |
| MultiPoint Connector |  | ✅ | ✅ | ✅ |
| Network ATC |  | ✅ | ✅ | ✅ |
| Network Controller |  | ❌ | ✅ | ✅ |
| Network Load Balancing |  | ✅ | ✅ | ✅ |
| Network Policy and Access Services |  | ✅³ | ✅³ | ✅³ |
| Network Virtualization |  | ✅ | ✅ | ✅ |
| Print and Document Services |  | ✅ | ✅ |  |
|  | Internet Printing | ✅³ | ✅³ | ✅³ |
|  | Line Printer Daemon (LPD) Service | ✅³ | ✅³ | ✅³ |
|  | Print Server | ✅³ | ✅³ | ✅³ |
| Quality Windows Audio Video Experience |  | ✅ | ✅ | ✅ |
| RAS Connection Manager Administration Kit (CMAK) |  | ✅ | ✅ | ✅ |
| Remote Access |  | ✅ | ✅ | ✅ |
|  | DirectAccess and VPN (RAS) | ✅ | ✅ | ✅ |
|  | Routing | ✅ | ✅ | ✅ |
|  | Web Application Proxy | ✅ | ✅ | ✅ |
| Remote Assistance |  | ✅³ | ✅³ | ✅³ |
| Remote Desktop Services |  | ✅³ | ✅³ | ✅³ |
| Remote Differential Compression |  | ✅ | ✅ | ✅ |
| Remote Server Administration Tools |  | ✅ | ✅ | ✅ |
| RPC over HTTP Proxy |  | ✅ | ✅ | ✅ |
| Setup and Boot Event Collection |  | ✅ | ✅ | ✅ |
| Simple TCP/IP Services |  | ✅³ | ✅³ | ✅³ |
| SNMP Service |  | ✅ | ✅ | ✅ |
| Software Load Balancer |  | ✅ | ✅ | ✅ |
| System Data Archiver |  | ✅ | ✅ | ✅ |
| System Insights |  | ✅ | ✅ | ✅ |
| Telnet Client |  | ✅ | ✅ | ✅ |
| TFTP Client |  | ✅³ | ✅³ | ✅³ |
| Virtualization |  | ✅ | ✅ | ✅ |
|  | Containers | ✅ | ✅ | ❌ |
|  | Hyper-V | ✅ | ✅ | ✅ |
|  | VM Shielding Tools for Fabric Management | ✅ | ✅ | ✅ |
| Volume Activation Services |  | ✅ | ✅ | ✅ |
| Web Server (IIS) |  | ✅ | ✅ | ✅ |
|  | FTP Server | ✅ | ✅ | ✅ |
|  | Web Server | ✅ | ✅ | ✅ |
| WebDAV Redirector |  | ✅ | ✅ | ✅ |
| Windows Biometric Framework |  | ✅³ | ✅³ | ✅³ |
| Windows Deployment Services |  | ✅ | ✅ | ✅ |
| Windows Identity Foundation 3.5 |  | ✅³ | ✅³ | ✅³ |
| Windows Internal Database |  | ✅ | ✅ | ✅ |
| Windows PowerShell |  | ✅ | ✅ | ✅ |
|  | Windows PowerShell 2.0 Engine | ✅ | ✅ | ✅ |
|  | Windows PowerShell 5.1 | ✅ | ✅ | ✅ |
|  | Windows PowerShell Desired State Configuration Service | ✅ | ✅ | ✅ |
|  | Windows PowerShell Web Access | ✅ | ✅ | ✅ |
| Windows Process Activation Service |  | ✅ | ✅ | ✅ |
| Windows Search Service |  | ✅³ | ✅³ | ✅³ |
| Windows Server Management enabled by Azure Arc |  | ✅⁴ | ✅⁴ | ✅⁴ |
|  | Azure Update Manager | ✅⁴ | ✅⁴ | ✅⁴ |
|  | Change Tracking and Inventory | ✅⁴ | ✅⁴ | ✅⁴ |
|  | Azure Machine Configuration | ✅⁴ | ✅⁴ | ✅⁴ |
|  | Windows Admin Center in Azure for Arc | ✅⁴ | ✅⁴ | ✅⁴ |
|  | Remote Support | ✅⁴ | ✅⁴ | ✅⁴ |
|  | Best Practices Assessment | ✅⁴ | ✅⁴ | ✅⁴ |
|  | Azure Site Recovery Configuration | ✅⁴ | ✅⁴ | ✅⁴ |
| Windows Server Backup |  | ✅ | ✅ | ✅ |
| Windows Server Migration Tools |  | ✅ | ✅ | ✅ |
| Windows Server Update Services |  | ✅ | ✅ | ✅ |
| Windows Standards-Based Storage Management |  | ✅ | ✅ | ✅ |
| Windows Subsystem for Linux |  | ✅ | ✅ | ✅ |
| Windows TIFF IFilter |  | ✅³ | ✅³ | ✅³ |
| WinRM IIS Extension |  | ✅ | ✅ | ✅ |
| WINS Server |  | ✅ | ✅ | ✅ |
| Wireless LAN Service |  | ✅ | ✅ | ✅ |
| WoW64 Support |  | ✅ | ✅ | ✅ |
| XPS Viewer |  | ✅³ | ✅³ | ✅³ |

1. As a guest if hosted on a virtualization host activated with Datacenter edition
2. Activated by Azure and can't be configured as a KMS host
3. When installed as Server with Desktop Experience
4. Available for machines enrolled in Windows Server Management enabled by Azure Arc with Windows Server licenses that have active Software Assurances or Windows Server licenses that with active subscription licenses. To learn more about the available Azure benefits, billing, and requirements, see [Windows Server Management enabled by Azure Arc](/en-us/azure/azure-arc/servers/windows-server-management-overview).

::: zone-end

::: zone pivot="windows-server-2019"

| Feature | Subfeature | Standard edition | Datacenter edition |
| --- | --- | --- | --- |
| .NET Framework 3.5 Features |  | ✅ | ✅ |
| .NET Framework 4.7 Features |  | ✅ | ✅ |
| Activation |  | ✅ | ✅ |
|  | Automatic Virtual Machine Activation | ⚠️¹ | ✅ |
|  | Key Management Service (KMS) | ✅ | ✅ |
| Active Directory Certificate Services |  | ✅ | ✅ |
|  | Certificate Enrollment Policy Web Service | ✅ | ✅ |
|  | Certificate Enrollment Web Service | ✅ | ✅ |
|  | Certification Authority | ✅ | ✅ |
|  | Certification Authority Web Enrollment | ✅ | ✅ |
|  | Network Device Enrollment Service | ✅ | ✅ |
|  | Online Responder | ✅ | ✅ |
| Active Directory Domain Services |  | ✅ | ✅ |
| Active Directory Federation Services |  | ✅ | ✅ |
| Active Directory Lightweight Directory Services |  | ✅ | ✅ |
| Active Directory Rights Management Services |  | ✅ | ✅ |
| Background Intelligent Transfer Service (BITS) |  | ✅ | ✅ |
| BitLocker Drive Encryption |  | ✅ | ✅ |
| BitLocker Network Unlock |  | ✅² | ✅² |
| BranchCache |  | ✅ | ✅ |
| Client for NFS |  | ✅ | ✅ |
| Data Center Bridging |  | ✅ | ✅ |
| Device Health Attestation |  | ✅ | ✅ |
| DHCP Server |  | ✅ | ✅ |
| Direct Play |  | ✅² | ✅² |
| DLNA codecs and web media streaming |  | ✅² | ✅² |
| DNS Server |  | ✅ | ✅ |
| Enhanced Storage |  | ✅ | ✅ |
| Failover Clustering |  | ✅ | ✅ |
| Fax Server |  | ✅ | ✅ |
| File and Storage Services |  | ✅ | ✅ |
|  | BranchCache for Network Files | ✅ | ✅ |
|  | Data Deduplication | ✅ | ✅ |
|  | DFS Namespaces | ✅ | ✅ |
|  | DFS Replication | ✅ | ✅ |
|  | File Server | ✅ | ✅ |
|  | File Server Resource Manager | ✅ | ✅ |
|  | File Server VSS Agent Service | ✅ | ✅ |
|  | iSCSI Target Server | ✅ | ✅ |
|  | iSCSI Target Storage Provider (VDS and VSS hardware providers) | ✅ | ✅ |
|  | Server for NFS | ✅ | ✅ |
|  | SMB 1.0/CIFS File Sharing Support | ✅ | ✅ |
|  | SMB Bandwidth Limit | ✅ | ✅ |
|  | Work Folders | ✅ | ✅ |
|  | Storage Migration Service | ✅ | ✅ |
|  | Storage Migration Service Proxy | ✅ | ✅ |
|  | Storage Spaces | ✅ | ✅ |
|  | Storage Spaces Direct | ❌ | ✅ |
|  | Storage Replica | ✅ | ✅ |
| Group Policy Management |  | ✅ | ✅ |
| Host Guardian Hyper-V Support |  | ❌ | ✅ |
| Host Guardian Service |  | ✅ | ✅ |
| I/O Quality of Service |  | ✅ | ✅ |
| IIS Hostable Web Core |  | ✅ | ✅ |
| IP Address Management (IPAM) Server |  | ✅ | ✅ |
| Internet Storage Name Server (iSNS) |  | ✅ | ✅ |
| Management OData IIS Extension |  | ✅ | ✅ |
| Media Foundation |  | ✅ | ✅ |
| Message Queuing |  | ✅ | ✅ |
|  | Message Queuing DCOM Proxy | ✅ | ✅ |
|  | Message Queuing Services | ✅ | ✅ |
| Microsoft Defender Antivirus |  | ✅ | ✅ |
| Multipath I/O |  | ✅ | ✅ |
| MultiPoint Connector |  | ✅ | ✅ |
| Network ATC |  | ✅ | ✅ |
| Network Controller |  | ❌ | ✅ |
| Network Load Balancing |  | ✅ | ✅ |
| Network Policy and Access Services |  | ✅² | ✅² |
| Network Virtualization |  | ✅ | ✅ |
| Print and Document Services |  | ✅ | ✅ |
|  | Internet Printing | ✅² | ✅² |
|  | Line Printer Daemon (LPD) Service | ✅² | ✅² |
|  | Print Server | ✅² | ✅² |
| Quality Windows Audio Video Experience |  | ✅ | ✅ |
| RAS Connection Manager Administration Kit (CMAK) |  | ✅ | ✅ |
| Remote Access |  | ✅ | ✅ |
|  | DirectAccess and VPN (RAS) | ✅ | ✅ |
|  | Routing | ✅ | ✅ |
|  | Web Application Proxy | ✅ | ✅ |
| Remote Assistance |  | ✅² | ✅² |
| Remote Desktop Services |  | ✅² | ✅² |
| Remote Differential Compression |  | ✅ | ✅ |
| Remote Server Administration Tools |  | ✅ | ✅ |
| RPC over HTTP Proxy |  | ✅ | ✅ |
| Setup and Boot Event Collection |  | ✅ | ✅ |
| Simple TCP/IP Services |  | ✅² | ✅² |
| SNMP Service |  | ✅ | ✅ |
| Software Load Balancer |  | ✅ | ✅ |
| System Data Archiver |  | ✅ | ✅ |
| System Insights |  | ✅ | ✅ |
| Telnet Client |  | ✅ | ✅ |
| TFTP Client |  | ✅² | ✅² |
| Virtualization |  | ✅ | ✅ |
|  | Containers | ✅ | ✅ |
|  | Hyper-V | ✅ | ✅ |
|  | VM Shielding Tools for Fabric Management | ✅ | ✅ |
| Volume Activation Services |  | ✅ | ✅ |
| Web Server (IIS) |  | ✅ | ✅ |
|  | FTP Server | ✅ | ✅ |
|  | Web Server | ✅ | ✅ |
| WebDAV Redirector |  | ✅ | ✅ |
| Windows Biometric Framework |  | ✅² | ✅² |
| Windows Deployment Services |  | ✅ | ✅ |
| Windows Identity Foundation 3.5 |  | ✅² | ✅² |
| Windows Internal Database |  | ✅ | ✅ |
| Windows PowerShell |  | ✅ | ✅ |
|  | Windows PowerShell 2.0 Engine | ✅ | ✅ |
|  | Windows PowerShell 5.1 | ✅ | ✅ |
|  | Windows PowerShell Desired State Configuration Service | ✅ | ✅ |
|  | Windows PowerShell Web Access | ✅ | ✅ |
| Windows Process Activation Service |  | ✅ | ✅ |
| Windows Search Service |  | ✅² | ✅² |
| Windows Server Backup |  | ✅ | ✅ |
| Windows Server Management enabled by Azure Arc³ |  | ✅ | ✅ |
|  | Azure Update Manager³ | ✅ | ✅ |
|  | Change Tracking and Inventory³ | ✅ | ✅ |
|  | Azure Machine Configuration³ | ✅ | ✅ |
|  | Windows Admin Center in Azure for Arc³ | ✅ | ✅ |
|  | Remote Support³ | ✅ | ✅ |
|  | Best Practices Assessment³ | ✅ | ✅ |
|  | Azure Site Recovery Configuration³ | ✅ | ✅ |
| Windows Server Migration Tools |  | ✅ | ✅ |
| Windows Server Update Services |  | ✅ | ✅ |
| Windows Standards-Based Storage Management |  | ✅ | ✅ |
| Windows Subsystem for Linux |  | ✅ | ✅ |
| Windows TIFF IFilter |  | ✅² | ✅² |
| WinRM IIS Extension |  | ✅ | ✅ |
| WINS Server |  | ✅ | ✅ |
| Wireless LAN Service |  | ✅ | ✅ |
| WoW64 Support |  | ✅ | ✅ |
| XPS Viewer |  | ✅² | ✅² |

1. As a guest if hosted on a virtualization host activated with Datacenter edition
2. When installed as Server with Desktop Experience
3. Available for machines enrolled in Windows Server Management enabled by Azure Arc with Windows Server licenses that have active Software Assurances or Windows Server licenses that with active subscription licenses. To learn more about the available Azure benefits, billing, and requirements, see [Windows Server Management enabled by Azure Arc](/en-us/azure/azure-arc/servers/windows-server-management-overview).

::: zone-end

::: zone pivot="windows-server-2016"

| Feature | Subfeature | Standard edition | Datacenter edition |
| --- | --- | --- | --- |
| .NET Framework 3.5 Features |  | ✅ | ✅ |
| .NET Framework 4.6 Features |  | ✅ | ✅ |
| Activation |  | ✅ | ✅ |
|  | Automatic Virtual Machine Activation | ⚠️¹ | ✅ |
|  | Key Management Service (KMS) | ✅ | ✅ |
| Active Directory Certificate Services |  | ✅ | ✅ |
|  | Certificate Enrollment Policy Web Service | ✅ | ✅ |
|  | Certificate Enrollment Web Service | ✅ | ✅ |
|  | Certification Authority | ✅ | ✅ |
|  | Certification Authority Web Enrollment | ✅ | ✅ |
|  | Network Device Enrollment Service | ✅ | ✅ |
|  | Online Responder | ✅ | ✅ |
| Active Directory Domain Services |  | ✅ | ✅ |
| Active Directory Federation Services |  | ✅ | ✅ |
| Active Directory Lightweight Directory Services |  | ✅ | ✅ |
| Active Directory Rights Management Services |  | ✅ | ✅ |
| Background Intelligent Transfer Service (BITS) |  | ✅ | ✅ |
| BitLocker Drive Encryption |  | ✅ | ✅ |
| BitLocker Network Unlock |  | ✅² | ✅² |
| BranchCache |  | ✅ | ✅ |
| Client for NFS |  | ✅ | ✅ |
| Data Center Bridging |  | ✅ | ✅ |
| Device Health Attestation |  | ✅ | ✅ |
| DHCP Server |  | ✅ | ✅ |
| Direct Play |  | ✅² | ✅² |
| DLNA codecs and web media streaming |  | ✅² | ✅² |
| DNS Server |  | ✅ | ✅ |
| Enhanced Storage |  | ✅ | ✅ |
| Failover Clustering |  | ✅ | ✅ |
| Fax Server |  | ✅ | ✅ |
| File and Storage Services |  | ✅ | ✅ |
|  | BranchCache for Network Files | ✅ | ✅ |
|  | Data Deduplication | ✅ | ✅ |
|  | DFS Namespaces | ✅ | ✅ |
|  | DFS Replication | ✅ | ✅ |
|  | File Server | ✅ | ✅ |
|  | File Server Resource Manager | ✅ | ✅ |
|  | File Server VSS Agent Service | ✅ | ✅ |
|  | iSCSI Target Server | ✅ | ✅ |
|  | iSCSI Target Storage Provider (VDS and VSS hardware providers) | ✅ | ✅ |
|  | Server for NFS | ✅ | ✅ |
|  | SMB 1.0/CIFS File Sharing Support | ✅ | ✅ |
|  | SMB Bandwidth Limit | ✅ | ✅ |
|  | Work Folders | ✅ | ✅ |
|  | Storage Spaces | ✅ | ✅ |
|  | Storage Spaces Direct | ❌ | ✅ |
|  | Storage Replica | ❌ | ✅ |
| Group Policy Management |  | ✅ | ✅ |
| Host Guardian Hyper-V Support |  | ❌ | ✅ |
| Host Guardian Service |  | ✅ | ✅ |
| I/O Quality of Service |  | ✅ | ✅ |
| IIS Hostable Web Core |  | ✅ | ✅ |
| IP Address Management (IPAM) Server |  | ✅ | ✅ |
| Internet Storage Name Server (iSNS) |  | ✅ | ✅ |
| Management OData IIS Extension |  | ✅ | ✅ |
| Media Foundation |  | ✅ | ✅ |
| Message Queuing |  | ✅ | ✅ |
|  | Message Queuing DCOM Proxy | ✅ | ✅ |
|  | Message Queuing Services | ✅ | ✅ |
| Microsoft Defender Antivirus |  | ✅ | ✅ |
| Multipath I/O |  | ✅ | ✅ |
| MultiPoint Connector |  | ✅ | ✅ |
| MultiPoint Services |  | ✅ | ✅ |
| Network ATC |  | ✅ | ✅ |
| Network Controller |  | ❌ | ✅ |
| Network Load Balancing |  | ✅ | ✅ |
| Network Policy and Access Services |  | ✅² | ✅² |
| Print and Document Services |  | ✅ | ✅ |
|  | Internet Printing | ✅² | ✅² |
|  | Line Printer Daemon (LPD) Service | ✅² | ✅² |
|  | Print Server | ✅² | ✅² |
|  | Distributed Scan Server | ✅² | ✅² |
| Quality Windows Audio Video Experience |  | ✅ | ✅ |
| RAS Connection Manager Administration Kit (CMAK) |  | ✅ | ✅ |
| Remote Access |  | ✅ | ✅ |
|  | DirectAccess and VPN (RAS) | ✅ | ✅ |
|  | Routing | ✅ | ✅ |
|  | Web Application Proxy | ✅ | ✅ |
| Remote Assistance |  | ✅² | ✅² |
| Remote Desktop Services |  | ✅² | ✅² |
| Remote Differential Compression |  | ✅ | ✅ |
| Remote Server Administration Tools |  | ✅ | ✅ |
| RPC over HTTP Proxy |  | ✅ | ✅ |
| Setup and Boot Event Collection |  | ✅ | ✅ |
| Simple TCP/IP Services |  | ✅² | ✅² |
| SNMP Service |  | ✅ | ✅ |
| Software Load Balancer |  | ✅ | ✅ |
| Telnet Client |  | ✅ | ✅ |
| TFTP Client |  | ✅² | ✅² |
| Virtualization |  | ✅ | ✅ |
|  | Containers | ✅ | ✅ |
|  | Hyper-V | ✅ | ✅ |
|  | VM Shielding Tools for Fabric Management | ✅ | ✅ |
| Volume Activation Services |  | ✅ | ✅ |
| Web Server (IIS) |  | ✅ | ✅ |
|  | FTP Server | ✅ | ✅ |
|  | Web Server | ✅ | ✅ |
| WebDAV Redirector |  | ✅ | ✅ |
| Windows Biometric Framework |  | ✅² | ✅² |
| Windows Deployment Services |  | ✅ | ✅ |
| Windows Identity Foundation 3.5 |  | ✅² | ✅² |
| Windows Internal Database |  | ✅ | ✅ |
| Windows PowerShell |  | ✅ | ✅ |
|  | Windows PowerShell 2.0 Engine | ✅ | ✅ |
|  | Windows PowerShell 5.1 | ✅ | ✅ |
|  | Windows PowerShell Desired State Configuration Service | ✅ | ✅ |
|  | Windows PowerShell Web Access | ✅ | ✅ |
| Windows Process Activation Service |  | ✅ | ✅ |
| Windows Server Essentials Experience |  | ✅ | ✅ |
| Windows Search Service |  | ✅² | ✅² |
| Windows Server Backup |  | ✅ | ✅ |
| Windows Server Management enabled by Azure Arc³ |  | ✅ | ✅ |
|  | Azure Update Manager³ | ✅ | ✅ |
|  | Change Tracking and Inventory³ | ✅ | ✅ |
|  | Azure Machine Configuration³ | ✅ | ✅ |
|  | Windows Admin Center in Azure for Arc³ | ✅ | ✅ |
|  | Remote Support³ | ✅ | ✅ |
|  | Best Practices Assessment³ | ✅ | ✅ |
|  | Azure Site Recovery Configuration³ | ✅ | ✅ |
| Windows Server Migration Tools |  | ✅ | ✅ |
| Windows Server Update Services |  | ✅ | ✅ |
| Windows Standards-Based Storage Management |  | ✅ | ✅ |
| Windows TIFF IFilter |  | ✅² | ✅² |
| WinRM IIS Extension |  | ✅ | ✅ |
| WINS Server |  | ✅ | ✅ |
| Wireless LAN Service |  | ✅ | ✅ |
| WoW64 Support |  | ✅ | ✅ |
| XPS Viewer |  | ✅² | ✅² |

1. As a guest if hosted on a virtualization host activated with Datacenter edition
2. When installed as Server with Desktop Experience
3. Available for machines enrolled in Windows Server Management enabled by Azure Arc with Windows Server licenses that have active Software Assurances or Windows Server licenses that with active subscription licenses. To learn more about the available Azure benefits, billing, and requirements, see [Windows Server Management enabled by Azure Arc](/en-us/azure/azure-arc/servers/windows-server-management-overview).

::: zone-end