---
layout: Conceptual
title: Deploy host networking with Network ATC | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/network-atc/network-atc
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to deploy host networking with Network ATC for Windows Server and Azure Local clusters. Simplify network configuration management using intent-based automation for compute, storage, and management networks.
author: robinharwood
ms.topic: how-to
ms.date: 2025-11-20T00:00:00.0000000Z
ms.author: roharwoo
ms.custom:
- ai-gen-docs-bap
- ai-gen-description
- ai-seo-date:07/18/2025
locale: en-us
document_id: fa98d531-5307-82b2-f61c-db11b0cb5efd
document_version_independent_id: fa98d531-5307-82b2-f61c-db11b0cb5efd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/network-atc/network-atc.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/network-atc/network-atc
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/network-atc/network-atc.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/289b8734-3abd-4162-bc19-e661c3f4c940
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a94795e-9024-410d-b38e-b67941440893
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: 0aa6b0ec-48ff-ef78-6aed-22486c5c948f
---

# Deploy host networking with Network ATC | Microsoft Learn

This article guides you through the requirements, best practices, and deployment of Network ATC. Network ATC simplifies the deployment and network configuration management for Windows Server and Azure Local clusters. Network ATC provides an intent-based approach to host network deployment. By specifying one or more intents (management, compute, or storage) for a network adapter, you can automate the deployment of the intended configuration. For more information on Network ATC, including an overview and definitions, see [Network ATC overview](/en-us/azure/azure-local/concepts/network-atc-overview?pivots=windows-server).

If you have feedback or encounter any issues, review the requirements and best practices section, check the Network ATC event log, and work with your Microsoft support team.

## Prerequisites

Complete the following prerequisites for using Network ATC:

- All servers in the cluster must be running Windows Server 2025 or later for Windows Server, and version 2311.2 or later for Azure Local environments.
- Must use physical hosts that are certified for Windows Server or Azure Local. For hardware certified for Secured-core server, see [Windows Server Catalog](https://www.windowsservercatalog.com/). For validated nodes or higher for Azure Local, see [Azure Local catalog](https://azurestackhcisolutions.azure.microsoft.com/).
- Adapters in the same Network ATC intent must be symmetric (of the same make, model, speed, and configuration) and available on each cluster node.

    - Asymmetric adapters lead to a failure in deploying any intent. Network ATC automatically confirms adapter symmetry for all nodes in the cluster before deploying an intent.
    - For more information on adapter symmetry, see [Switch Embedded Teaming (SET)](/en-us/azure/azure-local/concepts/host-network-requirements#switch-embedded-teaming-set).
- Each physical adapter specified in an intent must use the same name on all nodes in the cluster.
- Ensure each network adapter has an "Up" status, as verified by the PowerShell `Get-NetAdapter` cmdlet.
- Each node must have the following Windows Server features installed:

    - Network ATC
    - Hyper-V
    - Failover Clustering
    - Data Center Bridging
    - Failover cluster - SMB Bandwidth (FS-SMBBW)

    Here's an example of installing the required features via PowerShell:

    ```powershell
    Install-WindowsFeature -Name NetworkATC, Hyper-V, 'Failover-Clustering', 'Data-Center-Bridging', FS-SMBBW -IncludeManagementTools
    ```
- Insert each adapter in the same PCI slots in each host. This practice leads to ease in automated naming conventions by imaging systems.
- Configure the physical network (switches) before Network ATC including VLANs, MTU, and DCB configuration. For more information, please see [Physical Network Requirements](/en-us/azure/azure-local/concepts/physical-network-requirements).

Important

Deploying Network ATC in virtual machines might be used for test and validation purposes only. VM-based deployment requires an override to the default adapter settings to disable the NetworkDirect property. For more information on submission of an override, see: [Override default network settings](manage-network-atc#update-or-override-network-settings).

## Common Network ATC commands

To identify the available Network ATC commands, run the `Get-Command -ModuleName NetworkATC` cmdlet in PowerShell. Ensure PowerShell is run as an administrator.

The `Remove-NetIntent` cmdlet removes an intent from the local node or cluster. This command doesn't destroy the invoked configuration.

## Example intents

Network ATC modifies how you deploy host networking, not what you deploy. You can deploy multiple scenarios so long as each scenario is a supported scenario from Microsoft. Here are some examples of common deployment options, and the PowerShell commands needed. These scenarios aren't the only combinations available but they should give you an idea of the possibilities.

For simplicity we only demonstrate two physical adapters per SET team, however it's possible to add more. For more information, please see [Plan Host Networking](/en-us/azure/azure-local/concepts/host-network-requirements).

### Fully converged intent

For this intent, compute, storage, and management networks are deployed and managed across all cluster nodes.

[![Fully converged intent](../media/network-atc/network-atc-2-full-converge.png)](../media/network-atc/network-atc-2-full-converge.png#lightbox)

```powershell
Add-NetIntent -Name ConvergedIntent -Management -Compute -Storage -AdapterName pNIC01, pNIC02
```

### Converged compute and storage intent; separate management intent

Two intents are managed across cluster nodes. Management uses pNIC01, and pNIC02; Compute and storage are on different adapters.

[![Storage and compute converged intent](../media/network-atc/network-atc-3-separate-management-compute-storage.png)](../media/network-atc/network-atc-3-separate-management-compute-storage.png#lightbox)

```powershell
Add-NetIntent -Name Mgmt -Management -AdapterName pNIC01, pNIC02
Add-NetIntent -Name Compute_Storage -Compute -Storage -AdapterName pNIC03, pNIC04
```

### Fully disaggregated intent

For this intent, compute, storage, and management networks are all managed on different adapters across all cluster nodes.

[![Fully disaggregated intent](../media/network-atc/network-atc-4-fully-disaggregated.png)](../media/network-atc/network-atc-4-fully-disaggregated.png#lightbox)

```powershell
Add-NetIntent -Name Mgmt -Management -AdapterName pNIC01, pNIC02
Add-NetIntent -Name Compute -Compute -AdapterName pNIC03, pNIC04
Add-NetIntent -Name Storage -Storage -AdapterName pNIC05, pNIC06
```

### Storage-only intent

For this intent, only storage is managed. Network ATC doesn't manage the Management and compute adapters.

[![Storage only intent](../media/network-atc/network-atc-5-fully-disaggregated-storage-only.png)](../media/network-atc/network-atc-5-fully-disaggregated-storage-only.png#lightbox)

```powershell
Add-NetIntent -Name Storage -Storage -AdapterName pNIC05, pNIC06
```

### Compute and management intent

For this intent, compute and management networks are managed, but not storage.

[![Management and compute intent](../media/network-atc/network-atc-6-disaggregated-management-compute.png)](../media/network-atc/network-atc-6-disaggregated-management-compute.png#lightbox)

```powershell
Add-NetIntent -Name Management_Compute -Management -Compute -AdapterName pNIC01, pNIC02
```

### Multiple compute (switch) intents

For this intent, multiple compute switches are managed.

[![Multiple switches intent](../media/network-atc/network-atc-7-multiple-compute.png)](../media/network-atc/network-atc-7-multiple-compute.png#lightbox)

```powershell
Add-NetIntent -Name Compute1 -Compute -AdapterName pNIC03, pNIC04
Add-NetIntent -Name Compute2 -Compute -AdapterName pNIC05, pNIC06
```

## Default Network ATC values

Network ATC uses a set of default values to simplify the deployment and management of host networking. These defaults are applied when you create intents or modify network settings. Understanding these defaults can help you manage your network configuration effectively.

### Default values

This section describes other default values configured by Network ATC.

#### Default VLANs

Network ATC uses the following VLANs by default for adapters with the *storage* intent type. If the adapters are connected to a *physical* switch, these VLANs must be allowed on the physical network. If the adapters are switchless, no other configuration is required.

| Adapter Intent | Default Value |
| --- | --- |
| Management | Configured VLAN for management adapters isn't modified |
| Storage Adapter 1 | 711 |
| Storage Adapter 2 | 712 |
| Storage Adapter 3 | 713 |
| Storage Adapter 4 | 714 |
| Storage Adapter 5 | 715 |
| Storage Adapter 6 | 716 |
| Storage Adapter 7 | 717 |
| Storage Adapter 8 | 718 |
| Future Use | 719 |

Consider the following command:

```powershell
Add-NetIntent -Name MyIntent -Storage -AdapterName pNIC01, pNIC02, pNIC03, pNIC04
```

The physical NIC (or virtual NIC if necessary) is configured to use VLANs 711, 712, 713, and 714 respectively.

Note

Network ATC allows you to change the VLANs used with the `StorageVlans` parameter on `Add-NetIntent`.

#### Automatic storage IP addressing

Network ATC automatically configures valid IP Addresses for adapters with the *storage* intent type. Network ATC performs this configuration in a uniform manner across all nodes in your cluster and verifies that the address chosen isn't already in use on the network.

The default IP Address for each adapter on each node in the storage intent is set up as follows:

| Adapter | IP Address and Subnet | VLAN |
| --- | --- | --- |
| pNIC1 | 10.71.1.X | 711 |
| pNIC2 | 10.71.2.X | 712 |
| pNIC3 | 10.71.3.X | 713 |

To override Automatic Storage IP Addressing, create a storage override and pass the override when creating an intent:

```powershell
$StorageOverride = New-NetIntentStorageOverrides
$StorageOverride.EnableAutomaticIPGeneration = $false
```

```powershell
Add-NetIntent -Name MyIntent -Storage -Compute -AdapterName 'pNIC01', 'pNIC02' -StorageOverrides $StorageOverride
```

#### Cluster network settings

Network ATC configures a set of Cluster Network Features by default. The defaults are listed as follows:

| Property | Default |
| --- | --- |
| `EnableNetworkNaming` | ` $true` |
| `EnableLiveMigrationNetworkSelection` | `$true` |
| `EnableVirtualMachineMigrationPerformance` | `$true` |
| `VirtualMachineMigrationPerformanceOption` | Default is calculated: SMB, TCP, or Compression |
| `MaximumVirtualMachineMigrations` | 1 |
| `MaximumSMBMigrationBandwidthInGbps` | Default is calculated based on set-up |

### Default Data Center Bridging (DCB) configuration

Network ATC establishes the following priorities and bandwidth reservations. This configuration should also be configured on the physical network.

| Policy | Use | Default Priority | Default Bandwidth Reservation |
| --- | --- | --- | --- |
| Cluster | Cluster Heartbeat reservation | 7 | 2% if one or more adapters are &lt;= 10 Gbps; 1% if one or more adapters are &gt; 10 Gbps |
| SMB\_Direct | RDMA Storage Traffic | 3 | 50% |
| Default | All other traffic types | 0 | Remainder |

Note

Network ATC allows you to override default settings like default bandwidth reservation. For examples, see [Update or override network settings](manage-network-atc#update-or-override-network-settings).

## Common Error Messages

With the new event logs, there are some simplistic troubleshooting methods to identify intent deployment failures. This section outlines some of the common fixes when an issue is encountered. The following errors are from the output of the `Get-NetIntentStatus` cmdlet.

### Error: AdapterBindingConflict

[![Screenshot of Adapter Binding Error.](../media/network-atc/error-adapterbindingconflict.png)](../media/network-atc/error-adapterbindingconflict.png#lightbox)

Scenario 1: An adapter is bound to an existing vSwitch that conflicts with the new vSwitch that is being deployed by Network ATC.

**Solution:** Remove the conflicting vSwitch, then Set-NetIntentRetryState

Scenario 2: An adapter is bound to the component, but not necessarily a vSwitch.

**Solution:** Disable the vms\_pp component (unbind the adapter from the vSwitch) then run Set-NetIntentRetryState.

### Error: ConflictingTrafficClass

[![Screenshot of Conflicting Traffic Class error.](../media/network-atc/error-conflictingtrafficclass.png)](../media/network-atc/error-conflictingtrafficclass.png#lightbox)

This issue occurs because a traffic class is already configured. Network ATC is attempting to deploy traffic classes that conflict with this preconfigured traffic class. For example, you might have deployed a traffic class called SMB when Network ATC tries to deploy a similar traffic class with a different name.

**Solution:**

Clear the existing DCB configuration on the system then run Set-NetIntentRetryState

```powershell

Get-NetQosTrafficClass | Remove-NetQosTrafficClass
Get-NetQosPolicy | Remove-NetQosPolicy -Confirm:$false
Get-NetQosFlowControl | Disable-NetQosFlowControl
```

### Error: RDMANotOperational

[![Screenshot of RDMA Not Operational error.](../media/network-atc/error-rdmanotoperational.png)](../media/network-atc/error-rdmanotoperational.png#lightbox)

You might see this message:

1. If the network adapter uses an inbox driver. Inbox drivers aren't supported and must be updated.

    **Solution:** Upgrade the driver for the adapter.
2. If SR-IOV is disabled in the BIOS.

    **Solution:** Enable SR-IOV for the adapter in the system BIOS
3. If RDMA is disabled in the BIOS

    **Solution:** Enable RDMA for the adapter in the system BIOS

### Error: InvalidIsolationID

[![Screenshot of Invalid Isolation ID error.](../media/network-atc/error-invalidisolationid.png)](../media/network-atc/error-invalidisolationid.png#lightbox)

This message occurs when you use RoCE RDMA and override the default VLAN with an invalid value. Meaning the value you chose can't be used with that protocol. For example, RoCE RDMA requires a nonzero VLAN so that Priority Flow Control (PFC) markings can be added to the frame. A VLAN value between 1 - 4094 must be used. Network ATC doesn't override the value you specified without administrator intervention for several reasons. To resolve this issue:

1. Choose iWARP as the RDMA (NetworkDirect) protocol

    **Solution:** If supported by the adapter, Network ATC automatically chooses iWARP as its RDMA protocol that might use a VLAN ID of 0. Remove the override that enforces RoCE as the chosen protocol.
2. Use the default VLANs

    **Solution:** We highly recommend using the Network ATC Default VLANs
3. Use a valid VLAN

    When specifying a VLAN, use the -StorageVLANs parameter and specify comma separated values between 1 - 4094.