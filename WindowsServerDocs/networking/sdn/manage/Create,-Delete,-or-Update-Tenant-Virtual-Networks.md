---
layout: Conceptual
title: Create, delete, or update tenant virtual network | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/manage/create,-delete,-or-update-tenant-virtual-networks
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: In this topic, you learn how to create, delete, and update Hyper-V Network Virtualization Virtual Networks after you deploy Software Defined Networking (SDN). Hyper-V Network Virtualization helps you isolate tenant networks so that each tenant network is a separate entity. Each entity has no cross-connection possibility unless you configure public access workloads.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-11-02T00:00:00.0000000Z
locale: en-us
document_id: b3f802d7-55e5-b7e5-1095-5d198cbbcc6d
document_version_independent_id: 4053fee9-f2e5-19ba-b81c-706e25b01cd4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/manage/Create,-Delete,-or-Update-Tenant-Virtual-Networks.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/manage/create,-delete,-or-update-tenant-virtual-networks
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/manage/Create,-Delete,-or-Update-Tenant-Virtual-Networks.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
platformId: a1c58247-3df4-a433-62b7-0ffeec3bfa65
---

# Create, delete, or update tenant virtual network | Microsoft Learn

In this topic, you learn how to create, delete, and update Hyper-V Network Virtualization Virtual Networks after you deploy Software Defined Networking (SDN). Hyper-V Network Virtualization helps you isolate tenant networks so that each tenant network is a separate entity. Each entity has no cross-connection possibility unless you configure public access workloads.

## Create a new virtual network

Creating a virtual network for a tenant places it within a unique routing domain on the Hyper-V host. Beneath every virtual network, there is at least one virtual subnet. Virtual Subnets get defined by an IP prefix and reference a previously defined ACL.

The steps to create a new virtual network are:

1. Identify the IP address prefixes from which you want to create the virtual subnets.
2. Identify the logical provider network upon which the tenant traffic is tunneled.
3. Create at least one virtual subnet for each IP prefix that you identified in step 1.
4. (Optional) Add the previously created ACLs to the virtual subnets or add gateway connectivity for tenants.

The following table includes example subnet IDs and prefixes for two fictional tenants. The tenant Fabrikam has two virtual subnets, while the Contoso tenant has three virtual subnets.

| Tenant Name | Virtual Subnet ID | Virtual Subnet Prefix |
| --- | --- | --- |
| Fabrikam | 5001 | 24.30.1.0/24 |
| Fabrikam | 5002 | 24.30.2.0/20 |
| Contoso | 6001 | 24.30.1.0/24 |
| Contoso | 6002 | 24.30.2.0/24 |
| Contoso | 6003 | 24.30.3.0/24 |

The following example script uses Windows PowerShell commands exported from the **NetworkController** module to create Contoso's virtual network and one subnet:

```Powershell
import-module networkcontroller
$URI = "https://ncrest.contoso.local"

#Find the HNV Provider Logical Network

$logicalnetworks = Get-NetworkControllerLogicalNetwork -ConnectionUri $uri
foreach ($ln in $logicalnetworks) {
   if ($ln.Properties.NetworkVirtualizationEnabled -eq "True") {
      $HNVProviderLogicalNetwork = $ln
   }
}

#Find the Access Control List to user per virtual subnet

$acllist = Get-NetworkControllerAccessControlList -ConnectionUri $uri -ResourceId "AllowAll"

#Create the Virtual Subnet

$vsubnet = new-object Microsoft.Windows.NetworkController.VirtualSubnet
$vsubnet.ResourceId = "Contoso_WebTier"
$vsubnet.Properties = new-object Microsoft.Windows.NetworkController.VirtualSubnetProperties
$vsubnet.Properties.AccessControlList = $acllist
$vsubnet.Properties.AddressPrefix = "24.30.1.0/24"

#Create the Virtual Network

$vnetproperties = new-object Microsoft.Windows.NetworkController.VirtualNetworkProperties
$vnetproperties.AddressSpace = new-object Microsoft.Windows.NetworkController.AddressSpace
$vnetproperties.AddressSpace.AddressPrefixes = @("24.30.1.0/24")
$vnetproperties.LogicalNetwork = $HNVProviderLogicalNetwork
$vnetproperties.Subnets = @($vsubnet)
New-NetworkControllerVirtualNetwork -ResourceId "Contoso_VNet1" -ConnectionUri $uri -Properties $vnetproperties

```

## Modify an existing Virtual Network

You can use Windows PowerShell to update an existing Virtual subnet or network.

When you run the following example script, the updated resources are simply PUT to Network Controller with the same resource ID. If your tenant Contoso wants to add a new virtual subnet (24.30.2.0/24) to their virtual network, either you or the Contoso Administrator can use the following script.

```PowerShell
$acllist = Get-NetworkControllerAccessControlList -ConnectionUri $uri -ResourceId "AllowAll"

$vnet = Get-NetworkControllerVirtualNetwork -ResourceId "Contoso_VNet1" -ConnectionUri $uri

$vnet.properties.AddressSpace.AddressPrefixes += "24.30.2.0/24"

$vsubnet = new-object Microsoft.Windows.NetworkController.VirtualSubnet
$vsubnet.ResourceId = "Contoso_DBTier"
$vsubnet.Properties = new-object Microsoft.Windows.NetworkController.VirtualSubnetProperties
$vsubnet.Properties.AccessControlList = $acllist
$vsubnet.Properties.AddressPrefix = "24.30.2.0/24"

$vnet.properties.Subnets += $vsubnet

New-NetworkControllerVirtualNetwork -ResourceId "Contoso_VNet1" -ConnectionUri $uri -properties $vnet.properties

```

## Delete a Virtual Network

You can use Windows PowerShell to delete a Virtual Network.

The following Windows PowerShell example deletes a tenant Virtual Network by issuing an HTTP delete to the URI of the Resource ID.

```PowerShell
Remove-NetworkControllerVirtualNetwork -ResourceId "Contoso_Vnet1" -ConnectionUri $uri
```