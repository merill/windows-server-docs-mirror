---
layout: Conceptual
title: Configure alternative SMB ports for Windows Server 2025 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-ports
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: How to configure alternative SMB ports on Windows Server 2025
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2024-10-25T00:00:00.0000000Z
locale: en-us
document_id: 7770a03c-8c21-334e-7e5c-cad460ef48e9
document_version_independent_id: 7770a03c-8c21-334e-7e5c-cad460ef48e9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/file-server/smb-ports.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/file-server/smb-ports
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/file-server/smb-ports.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ca5e0a29-34da-4df5-1dc7-af90ccb188a4
---

# Configure alternative SMB ports for Windows Server 2025 | Microsoft Learn

You can use the SMB client to connect to alternative TCP, QUIC, and RDMA ports. However, you can only connect to alternative ports if the SMB server is configured to support listening on that port.

You can also configure your deployment to block configuring alternative ports or specify that ports can only connect to certain servers.

## Prerequisites

In order to configure alternative ports, you need the following:

- Your system must be running one of the following two operating systems:

    - Windows 11, version 24H2 or later
    - Windows Server 2025 or later
- Admin permissions
- An SMB server configured to listen to the port you want to use

## Map an alternative port

To map an alternative port to your SMB client:

# [PowerShell](#tab/powershell)
1. Open an elevated PowerShell window as an administrator.
2. Run one of the following commands to map a port:

    - Run this command to map a TCP port:

        ```powershell
        New-SmbMapping -LocalPath <drive letter>: -RemotePath \\server\share -TcpPort <port number between 0 and 65536>
        ```
    - Run this command to map a QUIC port:

        ```powershell
        New-SmbMapping -LocalPath <drive letter>: -RemotePath \\server\share -QuicPort <port number between 0 and 65536>
        ```
    - Run this command to map an RDMA port:

        ```powershell
        New-SmbMapping -LocalPath <drive letter>: -RemotePath \\server\share -RdmaPort <port number between 0 and 65536>
        ```

# [Command line](#tab/command-line)
1. Open an elevated command-line prompt as an administrator.
2. Run one of the following commands to map a port:

    - Run this command to map a TCP port:

        ```cmd
        NET USE <drive letter>: \\server\share /TCPPORT:<port number between 0 and 65536>
        ```
    - Run this command to map a QUIC port:

        ```cmd
        NET USE <drive letter>: \\server\share /QUICPORT:<port number between 0 and 65536>
        ```
    - Run this command to map an RDMA port:

        ```cmd
        NET USE <drive letter>: \\server\share /RDMAPORT:<port number between 0 and 65536>
        ```

---

## Control or block alternative port usage

The SMB server in Windows and Windows Server only supports changing the SMB over QUIC listening port. You can't configure TCP or RDMA listening ports.

The only method currently available to configure alternative ports is through PowerShell. You can configure the SMB over the QUIC server to use an alternative port by running the following commands:

```powershell
#Lists all available alternative ports
Get-SmbServerAlternativePort 

#Creates a new alternative port
New-SmbServerAlternativePort -TransportType QUIC -Port <port number> -EnableInstances Default

#Deletes an alternative port
Remove-SmbServerAlternativePort

#Configures SMB to use a specific port
Set-SmbServerAlternativePort
```