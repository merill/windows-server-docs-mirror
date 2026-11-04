---
layout: Conceptual
title: Configure Quality of Service (QoS) for a VM network adapter | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/manage/configure-qos-for-tenant-vm-network-adapter
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: You can configure SDN QoS for a VM network adapter to limit bandwidth on a virtual interface to prevent a high-traffic VM from blocking other users.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-11-02T00:00:00.0000000Z
locale: en-us
document_id: 357573cd-8c68-d9ec-42ab-5c08564b86b7
document_version_independent_id: 7579a9c8-17ef-8ce3-3183-22df3f6d94ac
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/manage/Configure-QoS-for-Tenant-VM-Network-Adapter.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/manage/configure-qos-for-tenant-vm-network-adapter
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/manage/Configure-QoS-for-Tenant-VM-Network-Adapter.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 778b7a6c-b81d-5f3f-6025-8b7a0fe98347
---

# Configure Quality of Service (QoS) for a VM network adapter | Microsoft Learn

You can configure Software Defined Networking (SDN) Quality of Service (QoS) for a virtual machine (VM) network adapter to limit bandwidth on a virtual interface to prevent a high-traffic VM from contending with other VM network traffic. You can also configure SDN QoS to reserve a specific amount of bandwidth for a VM to ensure that the VM can send traffic regardless of other traffic on the network. This can be applied to VMs attached to traditional VLAN networks as well as VMs attached to SDN overlay networks.

You can also configure ***QoS Offload*** to enforce QoS rules at the physical network adapter rather than at the virtual switch, resulting in lower CPU utilization and improved enforcement. QoS Offload is an optional capability found in Windows Server 2022 certified NICs that have achieved the Windows Server Software-Defined Data Center (SDDC) Premium Additional Qualification (AQ). For more information, see [Select a network adapter](/en-us/azure/azure-local/concepts/host-network-requirements#select-a-network-adapter?context=/windows-server/context/windows-server-edge-networking).

## SDN QoS bandwidth limits

SDN QoS provides configuration of maximum permitted send-side or receive-side bandwidth for VMs. This is supported for VMs connected to a traditional VLAN network as well as VMs connected to an SDN virtual network. Once set, your VM will not be able to send or receive traffic above the configured maximum limits. For a VM, you can choose to configure either a send-side limit, a receive-side limit, or both.

The settings that can be configured through SDN QoS are:

- **OutboundReservedValue** - If `outboundReservedMode` mode is "absolute", then the value indicates the bandwidth, in Mbps, guaranteed to the virtual port for transmission (egress). If `outboundReservedMode` mode is "weight", then the value indicates the weighted portion of the bandwidth guaranteed.
- **OutboundMaximumMbps** - Indicates the maximum permitted send-side bandwidth, in Mbps, for the virtual port (egress).
- **InboundMaximumMbps** - Indicates the maximum permitted receive-side bandwidth for the virtual port (ingress) in Mbps.

## SDN QoS policies

Once Network Controller for SDN is setup, you can go ahead and deploy your QoS policies. Today, you can do this using [Network Controller](/en-us/powershell/module/networkcontroller/?view=windowsserver2019-ps&amp;preserve-view=true) PowerShell cmdlets.

For all example scripts used below, `-ConnectionUri` is the REST URI of the Network Controller. For example: `https://nc.contoso.com`.

### Step 1: Configure global QoS settings

Run the following PowerShell command on a Network Controller computer or a management client of Network Controller. This will enable the global settings to configure QoS policies through Network Controller:

```powershell
$vswitchConfig=[Microsoft.Windows.NetworkController.VirtualSwitchManagerProperties]::new()
$qos=[Microsoft.Windows.NetworkController.VirtualSwitchQosSettings]::new()
$qos.EnableSoftwareReservations=$true
$vswitchConfig.QosSettings =$qos
Set-NetworkControllerVirtualSwitchConfiguration -ConnectionUri $uri -Properties $vswitchConfig
```

### Step 2: Configure QoS policies

First, you will need to identify the workload VM network interface where you want to apply the policy:

```powershell
$NwInterface=Get-NetworkControllerNetworkInterface -ConnectionUri $uri -ResourceId Vnet-VM2_Net_Adapter_0
```

Next, configure the inbound and outbound maximum throughput allowed on the network interface:

```powershell
$NwInterface.Properties.PortSettings.QosSettings= [Microsoft.Windows.NetworkController.VirtualNetworkInterfaceQosSettings]::new()
$NwInterface.Properties.PortSettings.QosSettings.InboundMaximumMbps ="1000"
New-NetworkControllerNetworkInterface -ConnectionUri $uri -ResourceId $NwInterface.ResourceId -Properties $NwInterface.Properties
```

## QoS Offload (optional)

You can configure the physical NIC to use QoS Offload. If your adapter supports QoS offload, ensure it is enabled using one of two methods:

- Network ATC (recommended)
- Manual enablement using the adapter properties

### Use Network ATC

QoS Offload is automatically enabled on all adapters with the `Compute` intent type. For more information, see [Simplify host networking with Network ATC](/en-us/azure/azure-local/deploy/network-atc?context=/windows-server/context/windows-server-edge-networking).

Note

This option is only available to Azure Local subscribers.

### Use manual enablement

Manual enablement is done through the built-in cmdlets used to manage the physical adapter properties.

Important

You must ensure that `QosOffload` is enabled on every physical NIC in the team across every host. Without this, the QoS rule will be enforced via the virtual switch and result in lower efficiency.

Use the following cmdlets to check if your adapters support `QosOffload` and then modify the adapter properties:

```powershell
Get-NetAdapterAdvancedProperty -Name <physical NIC Name> -RegistryKeyword *QosOffload
Enable QosOffload for your adapters:
Set-NetAdapterAdvancedProperty -Name  <physical NIC Name> -RegistryKeyword *QosOffload -RegistryValue 1
```

## Configure hardware QoS

You can configure hardware QoS using settings and policies.

### Step 1 - Configure global QoS settings

Perform the below steps on a Network Controller computer or a management client of Network Controller. This will enable the global setting to configure QoS policies through Network Controller.

```powershell
$vswitchConfig=[Microsoft.Windows.NetworkController.VirtualSwitchManagerProperties]::new()
$qos=[Microsoft.Windows.NetworkController.VirtualSwitchQosSettings]::new()
$qos.EnableHardwareLimits=$true
$vswitchConfig.QosSettings =$qos
Set-NetworkControllerVirtualSwitchConfiguration -ConnectionUri $uri -Properties $vswitchConfig
```

### Step 2 - Configure QoS policies

First, identify the workload VM network interface where you want to apply the policy:

```powershell
$NwInterface=Get-NetworkControllerNetworkInterface -ConnectionUri $uri -ResourceId Vnet-VM2_Net_Adapter_0
```

Next, configure the outbound maximum throughput allowed on the network interface. The following example creates a QoS rule limiting the outbound traffic from a VM interface to 1 Gbps.

Important

Qos Offload only supports **OutboundMaximumMbps**. You cannot use **OutboundReservedValue** or **InboundMaximumMbps** with Qos Offload.

```powershell
$NwInterface.Properties.PortSettings.QosSettings= [Microsoft.Windows.NetworkController.VirtualNetworkInterfaceQosSettings]::new()
$NwInterface.Properties.PortSettings.QosSettings. EnableHardwareLimits=$true
$NwInterface.Properties.PortSettings.QosSettings.OutboundMaximumMbps ="1000"
New-NetworkControllerNetworkInterface -ConnectionUri $uri -ResourceId $NwInterface.ResourceId -Properties $NwInterface.Properties
```

Note

During live migration, it is possible that a VM moves to a host that does not support QoS Offload. In this scenario, live migration will succeed, but QoS will fallback to SDN QoS.