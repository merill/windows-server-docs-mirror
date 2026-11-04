---
layout: Conceptual
title: Improve performance of a file server with SMB Direct | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-direct
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: SMB Direct allows for faster file transfer and more efficient network usage by utilizing remote direct memory access (RDMA) technology in Windows.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2025-01-16T00:00:00.0000000Z
ms.custom: os_security, network_security
locale: en-us
document_id: 85ab8371-7782-ad6f-b564-5fd93b3b879a
document_version_independent_id: 5d91cde1-786d-6c7b-f8c3-9667f9df84d7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/file-server/smb-direct.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/file-server/smb-direct
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/file-server/smb-direct.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 464d3d20-760e-be13-073d-0b1796a9c24c
---

# Improve performance of a file server with SMB Direct | Microsoft Learn

Windows Server includes a feature called Server Message Block (SMB) Direct, which supports the use of network adapters that have Remote Direct Memory Access (RDMA) capability. Network adapters that have RDMA can function at full speed with lower latency without compromising CPU utilization. For workloads such as Hyper-V or Microsoft SQL Server, this feature enables a remote file server to resemble local storage. SMB Direct is automatically configured and enabled by default in Windows Server 2012 and future iterations.

Using SMB Direct provides:

- **Increased throughput**: Applies the full throughput of high speed networks where the network adapters coordinate the transfer of large amounts of data at line speed.
- **Low latency**: Provides fast responses to network requests, which makes remote file storage feel like directly attached block storage.
- **Low CPU utilization**: Uses fewer CPU cycles when transferring data over the network, which leaves more power available to server applications.

You can use SMB Direct in a failover cluster; however, you need to make sure that the cluster networks used for client access are adequate for SMB Direct. Failover clustering supports using multiple networks for client access, along with network adapters that are RSS (Receive Side Scaling)-capable and RDMA-capable.

Note

You can use SMB Direct on the Hyper-V management operating system to support using Hyper-V over SMB, and to provide storage to a virtual machine that uses the Hyper-V storage stack. However, RDMA-capable network adapters aren't directly exposed to a Hyper-V client. Even if you connect an RDMA-capable network adapter to a virtual switch, the virtual network adapters created by the switch can't support RDMA.

## Requirements

The following are SMB Direct requirements:

- One or more network adapters with RDMA capability.
- At least two computers running one or more of the following operating systems:
    - Windows Server 2012 and later.
    - Windows 10 Enterprise and later.
    - Windows 10 Education and later.
    - Windows 10 Pro for Workstations and later
    - Windows 10 Pro 22H2 (clean install, not upgraded from older versions) and later.

Note

Windows 10 and Windows 11 family are restricted to client-only and can't act as an SMB Direct server.

### SMB Multichannel

SMB Multichannel is the feature responsible for detecting the RDMA capabilities of network adapters to enable SMB Direct. Without SMB Multichannel, SMB uses regular TCP/IP with the RDMA-capable network adapters (all network adapters provide a TCP/IP stack along with the new RDMA stack).

With SMB Multichannel, SMB detects whether a network adapter has RDMA capability, and creates multiple RDMA connections for that single session (two per interface). This feature allows SMB to use the high throughput, low latency, and low CPU utilization offered by RDMA-capable network adapters. It also offers fault tolerance if you're using multiple RDMA interfaces.

You can team RDMA-capable network adapters using Switch Embedded Teaming (SET) starting with Windows Server 2016. After at least one RDMA network connection is created, the TCP/IP connection used for the original protocol negotiation is no longer used. However, the TCP/IP connection is retained in case the RDMA network connections fail.

Disabling SMB Multichannel also disables SMB Direct. SMB Multichannel detects network adapter capabilities and determines whether a network adapter is RDMA-capable. Client devices can't use SMB Direct if SMB Multichannel is disabled.

### SMB Encryption

Beginning in Windows Server 2022 and Windows 11, SMB Direct now supports encryption. Previously, enabling SMB encryption disabled direct data placement, making RDMA performance as slow as TCP. Now data is encrypted before placement, leading to relatively minor performance degradation while adding AES-128 and AES-256 protected packet privacy. For more information on configuring SMB encryption, see [SMB security enhancements](smb-security).

Furthermore, Windows Server failover clusters now support granular control of encrypting intra-node storage communications for Cluster Shared Volumes (CSV) and the storage bus layer (SBL). This means that when using Storage Spaces Direct and SMB Direct, you can decide to encrypt east-west communications within the cluster itself for higher security.

## Disabling and enabling SMB Direct features

The SMB client automatically detects and uses multiple network connections if an appropriate configuration is identified. As SMB Direct is enabled by default, once disabled, it needs to be manually re-enabled whenever needed.

# [Disable](#tab/disable)
Typically, you don't need to disable SMB Direct, however, you can disable it along with its features, by running the following Windows PowerShell commands.

To disable SMB Direct, type:

```powershell
Disable-WindowsOptionalFeature -Online -FeatureName SMBDirect
```

To disable SMB Multichannel on the server-side, type:

```powershell
Set-SmbServerConfiguration -EnableMultiChannel $false
```

To disable SMB Multichannel on the client-side, type:

```powershell
Set-SmbClientConfiguration -EnableMultiChannel $false
```

To disable RDMA for a specific interface, type:

```powershell
Disable-NetAdapterRdma <name>
```

To disable RDMA for all interfaces, type:

```powershell
Set-NetOffloadGlobalSetting -NetworkDirect Disabled
```

When you disable RDMA on either the client or the server, the systems can't use it. *Network Direct* is the internal name for Windows Server basic networking support for RDMA interfaces.

# [Enable](#tab/enable)
After disabling SMB Direct and its features, you can re-enable them by running the following Windows PowerShell commands.

To enable SMB Direct, type:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName SMBDirect
```

To enable SMB Multichannel on the server-side, type:

```powershell
Set-SmbServerConfiguration -EnableMultiChannel $true
```

To enable SMB Multichannel on the client-side, type:

```powershell
Set-SmbClientConfiguration -EnableMultiChannel $true
```

To enable RDMA for a specific interface, type:

```powershell
Enable-NetAdapterRDMA <name>
```

To enable RDMA for all interfaces, type:

```powershell
Set-NetOffloadGlobalSetting -NetworkDirect Enabled
```

RDMA must be enabled on both the client and the server to start using it again.

---

To verify which state of operability SMB Direct is currently configured to, run the following cmdlet:

```powershell
Get-WindowsOptionalFeature -Online -FeatureName SMBDirect
```

## Testing SMB Direct

You can test the performance of SMB Direct by measuring the throughput when running a large file copy. Before testing, verify that the network adapter supports RDMA using PowerShell.

On the server-side, type:

```powershell
Get-SmbServerNetworkInterface
```

On the client-side, type:

```powershell
Get-SmbClientNetworkInterface
```

Once the network adapter is verified RDMA-capable, perform the following actions:

1. Disable RDMA on the network adapter, see Disabling and Enabling SMB Direct features.
2. Measure the amount of time taken to run a large file copy without using SMB Direct.
3. Re-enable RDMA on the network adapter, perform the same file copy, and then compare the two results.
4. To avoid the impact of caching, perform the following actions:
    1. Copy a large amount of data (more data than memory is capable of handling).
    2. Copy the data twice, with the first copy as practice and then timing the second copy.
    3. Restart both the server and the client before each test to ensure they operate under similar conditions.

Additionally, you can observe the performance counters during testing using the same scenario utilizing the Performance Monitor tool by performing the following steps:

1. Select **Start**, type **perfmon**, hit Enter.
2. In the left pane, under **Monitoring Tools** &gt; select **Performance Monitor**.
3. In the right pane, select the green "**+**" icon to add a new counter.
4. In the **Add Counters** dialog box, expand **SMB Direct Connection**.
5. Select both **Bytes RDMA Read/sec** and **Bytes RDMA Written/sec**, select **Add**, then select **OK**.

## SMB Direct failover capability

Here's how to confirm the failover capability of SMB Direct:

1. Ensure that SMB Direct is functioning in a multiple network adapter configuration.
2. Run a large file copy. During the copy process, simulate a failure of one of the network paths by disconnecting one of the cables or by disabling one of the network adapters.
3. Confirm that the file copying continues using one of the remaining network adapters, and that there are no file copy errors.

Tip

To avoid failures of a workload that doesn't use SMB Direct, make sure there are no other workloads using the disconnected network path.