---
layout: Conceptual
title: Configure virtual network peering | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/vnet-peering/sdn-configure-vnet-peering
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: Configuring the virtual network peering involves creating two virtual networks that get peered.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-11-04T00:00:00.0000000Z
locale: en-us
document_id: 41665e20-342b-7159-fb70-7124b4032877
document_version_independent_id: 9fd51973-a722-0ffe-c013-045d1b95c1e1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/vnet-peering/sdn-configure-vnet-peering.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/vnet-peering/sdn-configure-vnet-peering
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/vnet-peering/sdn-configure-vnet-peering.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
platformId: 469b25f2-740d-0261-b973-e500d32c76df
---

# Configure virtual network peering | Microsoft Learn

In this procedure, you use Windows PowerShell to create two virtual networks, each with one subnet. Then, you configure peering between the two virtual networks to enable connectivity between them.

- Step 1. Create the first virtual network
- Step 2. Create the second virtual network
- Step 3. Configure peering from the first virtual network to the second virtual network
- Step 4. Configure peering from the second virtual network to the first virtual network

Important

Remember to update the properties for your environment.

## Step 1: Create the first virtual network

In this step, you use Windows PowerShell find the HNV provider logical network to create the first virtual network with one subnet. The following example script creates Contoso's virtual network with one subnet.

```PowerShell
#Find the HNV Provider Logical Network

$logicalnetworks = Get-NetworkControllerLogicalNetwork -ConnectionUri $uri
foreach ($ln in $logicalnetworks) {
   if ($ln.Properties.NetworkVirtualizationEnabled -eq "True") {
      $HNVProviderLogicalNetwork = $ln
   }
}

#Create the Virtual Subnet

$vsubnet = new-object Microsoft.Windows.NetworkController.VirtualSubnet
$vsubnet.ResourceId = "Contoso"
$vsubnet.Properties = new-object Microsoft.Windows.NetworkController.VirtualSubnetProperties
$vsubnet.Properties.AddressPrefix = "24.30.1.0/24"
$uri=”https://restserver”

#Create the Virtual Network

$vnetproperties = new-object Microsoft.Windows.NetworkController.VirtualNetworkProperties
$vnetproperties.AddressSpace = new-object Microsoft.Windows.NetworkController.AddressSpace
$vnetproperties.AddressSpace.AddressPrefixes = @("24.30.1.0/24")
$vnetproperties.LogicalNetwork = $HNVProviderLogicalNetwork
$vnetproperties.Subnets = @($vsubnet)
New-NetworkControllerVirtualNetwork -ResourceId "Contoso_VNet1" -ConnectionUri $uri -Properties $vnetproperties
```

## Step 2: Create the second virtual network

In this step, you create a second virtual network with one subnet. The following example script creates Woodgrove's virtual network with one subnet.

```PowerShell

#Create the Virtual Subnet

$vsubnet = new-object Microsoft.Windows.NetworkController.VirtualSubnet
$vsubnet.ResourceId = "Woodgrove"
$vsubnet.Properties = new-object Microsoft.Windows.NetworkController.VirtualSubnetProperties
$vsubnet.Properties.AddressPrefix = "24.30.2.0/24"
$uri=”https://restserver”

#Create the Virtual Network

$vnetproperties = new-object Microsoft.Windows.NetworkController.VirtualNetworkProperties
$vnetproperties.AddressSpace = new-object Microsoft.Windows.NetworkController.AddressSpace
$vnetproperties.AddressSpace.AddressPrefixes = @("24.30.2.0/24")
$vnetproperties.LogicalNetwork = $HNVProviderLogicalNetwork
$vnetproperties.Subnets = @($vsubnet)
New-NetworkControllerVirtualNetwork -ResourceId "Woodgrove_VNet1" -ConnectionUri $uri -Properties $vnetproperties
```

## Step 3: Configure peering from the first virtual network to the second virtual network

In this step, you configure the peering between the first virtual network and the second virtual network you created in the previous two steps. The following example script establishes virtual network peering from **Contoso\_vnet1** to **Woodgrove\_vnet1**.

```PowerShell
$peeringProperties = New-Object Microsoft.Windows.NetworkController.VirtualNetworkPeeringProperties
$vnet2 = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "Woodgrove_VNet1"
$peeringProperties.remoteVirtualNetwork = $vnet2

#Indicate whether communication between the two virtual networks
$peeringProperties.allowVirtualnetworkAccess = $true

#Indicates whether forwarded traffic is allowed across the vnets
$peeringProperties.allowForwardedTraffic = $true

#Indicates whether the peer virtual network can access this virtual networks gateway
$peeringProperties.allowGatewayTransit = $false

#Indicates whether this virtual network uses peer virtual networks gateway
$peeringProperties.useRemoteGateways =$false

New-NetworkControllerVirtualNetworkPeering -ConnectionUri $uri -VirtualNetworkId “Contoso_vnet1” -ResourceId “ContosotoWoodgrove” -Properties $peeringProperties

```

Important

After creating this peering, the vnet status shows **Initiated**.

## Step 4: Configure peering from the second virtual network to the first virtual network

In this step, you configure the peering between the second virtual network and the first virtual network you created in steps 1 and 2 above. The following example script establishes virtual network peering from **Woodgrove\_vnet1** to **Contoso\_vnet1**.

```PowerShell
$peeringProperties = New-Object Microsoft.Windows.NetworkController.VirtualNetworkPeeringProperties
$vnet2=Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "Contoso_VNet1"
$peeringProperties.remoteVirtualNetwork = $vnet2

# Indicates whether communication between the two virtual networks is allowed
$peeringProperties.allowVirtualnetworkAccess = $true

# Indicates whether forwarded traffic will be allowed across the vnets
$peeringProperties.allowForwardedTraffic = $true

# Indicates whether the peer virtual network can access this virtual network's gateway
$peeringProperties.allowGatewayTransit = $false

# Indicates whether this virtual network will use peer virtual network's gateway
$peeringProperties.useRemoteGateways =$false

New-NetworkControllerVirtualNetworkPeering -ConnectionUri $uri -VirtualNetworkId “Woodgrove_vnet1” -ResourceId “WoodgrovetoContoso” -Properties $peeringProperties

```

After creating this peering, the vnet peering status shows **Connected** for both the peers. Now, virtual machines in one virtual network can communicate with virtual machines in the peered virtual network.