---
layout: Conceptual
title: Connect container endpoints to a tenant virtual network | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/manage/connect-container-endpoints-to-a-tenant-virtual-network
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: In this topic, we show you how to connect container endpoints to an existing tenant virtual network created through SDN. You use the l2bridge (and optionally l2tunnel) network driver available with the Windows libnetwork plugin for Docker to create a container network on the tenant VM.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-11-02T00:00:00.0000000Z
locale: en-us
document_id: 077a4685-0ed1-265b-fa9e-55d9c85e95ac
document_version_independent_id: 35ddbe17-fa40-64cc-a7bc-814f69bdb9e6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/manage/Connect-container-endpoints-to-a-Tenant-Virtual-Network.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/manage/connect-container-endpoints-to-a-tenant-virtual-network
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/manage/Connect-container-endpoints-to-a-Tenant-Virtual-Network.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 6a397350-809a-ccf0-3f4e-37b292584856
---

# Connect container endpoints to a tenant virtual network | Microsoft Learn

In this topic, we show you how to connect container endpoints to an existing tenant virtual network created through SDN. You use the *l2bridge* (and optionally *l2tunnel*) network driver available with the Windows libnetwork plugin for Docker to create a container network on the tenant VM.

In the [Container network drivers](/en-us/virtualization/windowscontainers/container-networking/network-drivers-topologies) topic, we discussed the multiple network drivers are available through Docker on Windows. For SDN, use the *l2bridge* and *l2tunnel* drivers. For both drivers, each container endpoint is in the same virtual subnet as the container host (tenant) virtual machine.

The Host Networking Service (HNS), through the private cloud plugin, dynamically assigns the IP addresses for container endpoints. The container endpoints have unique IP addresses but share the same MAC address of the container host (tenant) virtual machine due to Layer-2 address translation.

Network policy (ACLs, encapsulation, and QoS) for these container endpoints are enforced in the physical Hyper-V host as received by the Network Controller and defined in upper-layer management systems.

The differences between the *l2bridge* and *l2tunnel* drivers are:

| l2bridge | l2tunnel |
| --- | --- |
| Container endpoints that reside on: <br>- The same container host virtual machine and on the same subnet have all network traffic bridged within the Hyper-V virtual switch.<br>- Different container host VMs or on different subnets have their traffic forwarded to the physical Hyper-V host.<br><br>Network policy does not get enforced since network traffic between containers on the same host and in the same subnet do not flow to the physical host. Network policy applies only to cross-host or cross-subnet container network traffic. | *ALL* network traffic between two container endpoints is forwarded to the physical Hyper-V host regardless of host or subnet. Network policy applies to both cross-subnet and cross-host network traffic. |

Note

These networking modes do not work for connecting windows container endpoints to a tenant virtual network in Azure public cloud.

## Prerequisites

- A deployed SDN infrastructure with the Network Controller.
- A tenant virtual network has been created.
- A deployed tenant virtual machine with the Windows Container feature enabled, Docker installed, and Hyper-V feature enabled. The Hyper-V feature is required to install several binaries for l2bridge and l2tunnel networks.

    ```powershell
    # To install HyperV feature without checks for nested virtualization
    dism /Online /Enable-Feature /FeatureName:Microsoft-Hyper-V /All
    ```

Note

[Nested virtualization](/en-us/virtualization/hyper-v-on-windows/user-guide/nested-virtualization) and exposing virtualization extensions is not required unless using Hyper-V Containers.

## Workflow

1. Add multiple IP configurations to an existing VM NIC resource through Network Controller (Hyper-V Host)2. Enable the network proxy on the host to allocate CA IP Addresses for container endpoints (Hyper-V Host)3. Install the private cloud plug-in to assign CA IP addresses to container endpoints (Container Host VM)4. Create an *l2bridge* or *l2tunnel* network using docker (Container Host VM)

Note

Multiple IP configurations is not supported on VM NIC resources created through System Center Virtual Machine Manager. It is recommended for these deployments types that you create the VM NIC resource out of band using Network Controller PowerShell.

### 1. Add Multiple IP Configurations

In this step, we assume the VM NIC of the tenant virtual machine has one IP configuration with IP address of 192.168.1.9 and is attached to a VNet Resource ID of 'VNet1' and VM Subnet Resource of 'Subnet1' in the 192.168.1.0/24 IP subnet. We add 10 IP addresses for containers from 192.168.1.101 - 192.168.1.110.

```powershell
Import-Module NetworkController

# Specify Network Controller REST IP or FQDN
$uri = "<NC REST IP or FQDN>"
$vnetResourceId = "VNet1"
$vsubnetResourceId = "Subnet1"

$vmnic= Get-NetworkControllerNetworkInterface -ConnectionUri $uri | where {$_.properties.IpConfigurations.Properties.PrivateIPAddress -eq "192.168.1.9" }
$vmsubnet = Get-NetworkControllerVirtualSubnet -VirtualNetworkId $vnetResourceId -ResourceId $vsubnetResourceId -ConnectionUri $uri

# For this demo, we will assume an ACL has already been defined; any ACL can be applied here
$allowallacl = Get-NetworkControllerAccessControlList -ConnectionUri $uri -ResourceId "AllowAll"

foreach ($i in 1..10)
{
    $newipconfig = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfiguration
    $props = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfigurationProperties

    $resourceid = "IP_192_168_1_1"
    if ($i -eq 10)
    {
        $resourceid += "10"
        $ipstr = "192.168.1.110"
    }
    else
    {
        $resourceid += "0$i"
        $ipstr = "192.168.1.10$i"
    }

    $newipconfig.ResourceId = $resourceid
    $props.PrivateIPAddress = $ipstr

    $props.PrivateIPAllocationMethod = "Static"
    $props.Subnet = new-object Microsoft.Windows.NetworkController.Subnet
    $props.Subnet.ResourceRef = $vmsubnet.ResourceRef
    $props.AccessControlList = new-object Microsoft.Windows.NetworkController.AccessControlList
    $props.AccessControlList.ResourceRef = $allowallacl.ResourceRef

    $newipconfig.Properties = $props
    $vmnic.Properties.IpConfigurations += $newipconfig
}

New-NetworkControllerNetworkInterface -ResourceId $vmnic.ResourceId -Properties $vmnic.Properties -ConnectionUri $uri
```

### 2. Enable the network proxy

In this step, you enable the network proxy to allocate multiple IP addresses for the container host virtual machine.

To enable the network proxy, run the [ConfigureMCNP.ps1](https://github.com/Microsoft/SDN/blob/master/Containers/ConfigureMCNP.ps1) script on the **Hyper-V Host** hosting the container host (tenant) virtual machine.

```powershell
PS C:\> ConfigureMCNP.ps1
```

### 3. Install the Private Cloud plug-in

In this step, you install a plug-in to allow the HNS to communicate with the network proxy on the Hyper-V Host.

To install the plug-in, run the [InstallPrivateCloudPlugin.ps1](https://github.com/Microsoft/SDN/blob/master/Containers/InstallPrivateCloudPlugin.ps1) script inside the **container host (tenant) virtual machine**.

```powershell
PS C:\> InstallPrivateCloudPlugin.ps1
```

### 4. Create an *l2bridge* Container Network

In this step, you use the `docker network create` command on the **container host (tenant) virtual machine** to create an l2bridge network.

```powershell
# Create the container network
C:\> docker network create -d l2bridge --subnet="192.168.1.0/24" --gateway="192.168.1.1" MyContainerOverlayNetwork

# Attach a container to the MyContainerOverlayNetwork
C:\> docker run -it --network=MyContainerOverlayNetwork <image> <cmd>
```

Note

Static IP assignment is not supported with *l2bridge* or *l2tunnel* container networks when used with the Microsoft SDN Stack.

## More information

For more details about deploying an SDN infrastructure, see [Deploy a Software Defined Network Infrastructure](../deploy/deploy-a-software-defined-network-infrastructure).