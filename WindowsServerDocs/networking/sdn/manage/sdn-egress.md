---
layout: Conceptual
title: Egress metering in virtual network | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/manage/sdn-egress
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: A fundamental aspect of cloud networking monetization is network bandwidth egress, for example, outbound data transfers in the Microsoft Azure business model. Outbound data is charged based on the total amount of data moving out of the Azure datacenters via the internet in a given billing cycle.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2018-10-02T00:00:00.0000000Z
locale: en-us
document_id: 607370b9-137e-e618-021f-0f7248a2c409
document_version_independent_id: 25494545-9934-c400-cdf0-5e20f4c5fe50
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/manage/sdn-egress.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/manage/sdn-egress
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/manage/sdn-egress.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 5f624ce9-5f10-7e27-0c6c-1a0d73a625a9
---

# Egress metering in virtual network | Microsoft Learn

A fundamental aspect of cloud networking monetization is being able to bill by network bandwidth utilization. Outbound data is charged based on the total amount of data moving out of the data center via the Internet in a given billing cycle.

Egress metering for SDN network traffic in Windows Server 2019 enables the ability to offer usage meters for outbound data transfers. Network traffic that leaves each virtual network but remains within the data center can be tracked separately so it can be excluded from billing calculations. Packets bound for destination IP addresses that are not included in one of the unbilled address ranges are tracked as billed outbound data transfers.

## Virtual network unbilled address ranges (allow list of IP ranges)

You can find unbilled address ranges under the **UnbilledAddressRanges** property of an existing virtual Network. By default, there are no address ranges added.

```PowerShell
import-module NetworkController
$uri = "https://sdn.contoso.com"

(Get-NetworkControllerVirtualNetwork -ConnectionURI $URI -ResourceId "VNet1").properties
```

Your output will look similar to this:

```
 AddressSpace           : Microsoft.Windows.NetworkController.AddressSpace
 DhcpOptions            :
 UnbilledAddressRanges  :
 ConfigurationState     :
 ProvisioningState      : Succeeded
 Subnets                : {21e71701-9f59-4ee5-b798-2a9d8c2762f0, 5f4758ef-9f96-40ca-a389-35c414e996cc,
                      29fe67b8-6f7b-486c-973b-8b9b987ec8b3}
 VirtualNetworkPeerings :
 EncryptionCredential   :
 LogicalNetwork         : Microsoft.Windows.NetworkController.LogicalNetwork
```

## Example: Manage the unbilled address ranges of a virtual network

You can manage the set of IP subnet prefixes to exclude from billed egress metering by setting the **UnbilledAddressRange** property of a virtual network. Any traffic sent by network interfaces on the virtual network with a destination IP address that matches one of the prefixes will not be included in the BilledEgressBytes property.

1. Update the **UnbilledAddressRanges** property to contain the subnets that will not be billed for access.

    ```PowerShell
    $vnet = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceID "VNet1"
    $vnet.Properties.UnbilledAddressRanges = "10.10.2.0/24,10.10.3.0/24"
    ```

    Tip

    If adding multiple IP subnets, use a comma between each of the IP subnets. Do not include any spaces before or after the comma.
2. Update the Virtual Network resource with the modified **UnbilledAddressRanges** property.

    ```PowerShell
    New-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "VNet1" -Properties $unbilled.Properties -PassInnerException
    ```

    Your output will look similar to this:

    ```
       Confirm
       Performing the operation 'New-NetworkControllerVirtualNetwork' on entities of type
       'Microsoft.Windows.NetworkController.VirtualNetwork' via
       'https://sdn.contoso.com/networking/v3/virtualNetworks/VNet1'. Are you sure you want to continue?
       [Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

       Tags             :
       ResourceRef      : /virtualNetworks/VNet1
       InstanceId       : 29654b0b-9091-4bed-ab01-e172225dc02d
       Etag             : W/"6970d0a3-3444-41d7-bbe4-36327968d853"
       ResourceMetadata :
       ResourceId       : VNet1
       Properties       : Microsoft.Windows.NetworkController.VirtualNetworkProperties
    ```
3. Check the Virtual Network to see the configured **UnbilledAddressRanges**.

    ```PowerShell
    (Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceID "VNet1").properties
    ```

    Your output will now look similar to this:

    ```
    AddressSpace           : Microsoft.Windows.NetworkController.AddressSpace
    DhcpOptions            :
    UnbilledAddressRanges  : 10.10.2.0/24,192.168.2.0/24
    ConfigurationState     :
    ProvisioningState      : Succeeded
    Subnets                : {21e71701-9f59-4ee5-b798-2a9d8c2762f0, 5f4758ef-9f96-40ca-a389-35c414e996cc,
                         29fe67b8-6f7b-486c-973b-8b9b987ec8b3}
    VirtualNetworkPeerings :
    EncryptionCredential   :
    LogicalNetwork         : Microsoft.Windows.NetworkController.LogicalNetwork
    ```

## Check the billed the unbilled egress usage of a virtual network

After you configure the **UnbilledAddressRanges** property, you can check the billed and unbilled egress usage of each subnet within a virtual network. Egress traffic updates every four minutes with the total bytes of the billed and unbilled ranges.

The following properties are available for each virtual subnet:

- **UnbilledEgressBytes** shows the number of unbilled bytes sent by network interfaces connected to this virtual subnet. Unbilled bytes are bytes sent to address ranges that are part of the **UnbilledAddressRanges** property of the parent virtual network.
- **BilledEgressBytes** shows Number of billed bytes sent by network interfaces connected to this virtual subnet. Billed bytes are bytes sent to address ranges that are not part of the **UnbilledAddressRanges** property of the parent virtual network.

Use the following example to query egress usage:

```PowerShell
(Get-NetworkControllerVirtualNetwork -ConnectionURI $URI -ResourceId "VNet1").properties.subnets.properties | ft AddressPrefix,BilledEgressBytes,UnbilledEgressBytes
```

Your output will look similar to this:

```
AddressPrefix BilledEgressBytes UnbilledEgressBytes
------------- ----------------- -------------------
10.0.255.8/29          16827067                   0
10.0.2.0/24           781733019                   0
10.0.4.0/24                   0                   0
```