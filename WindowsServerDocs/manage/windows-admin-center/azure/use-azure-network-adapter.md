---
layout: Conceptual
title: Connect server to Azure Virtual Network - Azure Network Adapter | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/azure/use-azure-network-adapter
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: This article provides requirements and steps on how to use Azure Network Adapter to connect a server to an Azure Virtual Network.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2020-07-14T00:00:00.0000000Z
ms.contributors: thmaure-08202021
ms.custom:
- team=cloud_advocates
- sfi-image-nochange
locale: en-us
document_id: 2f200af5-2b04-a0f4-51c2-863028acc0be
document_version_independent_id: e54ed97b-c453-fbbe-cc03-b306a88065f6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/azure/use-azure-network-adapter.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/azure/use-azure-network-adapter
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/azure/use-azure-network-adapter.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b80e2359-d576-88f8-9201-fb08403ead26
---

# Connect server to Azure Virtual Network - Azure Network Adapter | Microsoft Learn

A lot of workloads running on-premises and in multi-cloud environments require connections to virtual machines (VMs) running in Microsoft Azure. To connect a server to an Azure Virtual Network, you have several options, including Site-to-Site VPN, Azure Express Route, and Point-to-Site VPN.

Windows Admin Center and Azure Network Adapter provide a one-click experience to connect the server with your virtual network using a [Point-to-Site VPN](/en-us/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal) connection. The process automates configuring the virtual network gateway and the on-premises VPN client.

## When to use Azure Network Adapter

Azure Network Adapter Point-to-Site VPN connections are useful when you want to connect to your virtual network from a remote location, such as a branch office, store, or other location. You can also use Azure Network Adapter instead of a Site-to-Site VPN when you require only a few servers to connect to a virtual network. Azure Network Adapter connections don't require a VPN device or a public-facing IP address.

### Requirements

Using Azure Network Adapter to connect to a virtual network requires the following:

- An Azure account with at least one active subscription.
- An existing virtual network.
- Internet access for the target servers that you want to connect to the Azure virtual network.
- A Windows Admin Center connection to Azure. To learn more, see [Configuring Azure integration](/en-us/windows-server/manage/windows-admin-center/azure/azure-integration).
- The latest version of Windows Admin Center. To learn more, see [Windows Admin Center](https://www.microsoft.com/windows-server/windows-admin-center).

Note

It’s not required to install Windows Admin Center on the server that you want to connect to Azure. However, you can do that in a single server scenario.

## Add an Azure Network Adapter to a server

To configure Azure Network Adapter, go to the Network extension for it in Windows Admin Center.

In Windows Admin Center:

1. Navigate to the server hosting the VMs that you want to add to Azure Network Adapter.
2. Under **Tools**, select **Networks**.
3. Select **Add Azure Network Adapter**.
4. On the **Add Azure Network Adapter** pane, enter the following required information, and then select **Create**:
    - **Subscription**
    - **Location**
    - **Virtual Network**
    - **Gateway Subnet** (if doesn’t exist)
    - **Gateway SKU** (if doesn’t exist)
    - **Client Address Space**

        The client address pool is a range of private IP addresses that you specify. The clients that connect over a Point-to-Site VPN dynamically receive an IP address from this range. Use a private IP address range that does not overlap with the on-premises location that you connect from, or the virtual network that you want to connect to. We recommend using IP addresses that are in the ranges designated for private networks (10.x.x.x, 192.168.x.x, or 172.16.0.0 to 172.31.255.255).
    - **Authentication Certificate**

        Azure uses certificates to authenticate clients connecting to a virtual network over a Point-to-Site VPN connection. The public key information of the root certificate is uploaded to Azure. The root certificate is then considered “trusted” by Azure for a Point-to-Site connection to the virtual network. Client certificates must be generated from the trusted root certificate and installed on the client server. The client certificate is used to authenticate the client when it initiates a connection to the virtual network.

        To learn more, see the “Configure authentication type” section of [Configure a Point-to-Site VPN connection to a VNet using native Azure certificate authentication: Azure portal](/en-us/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal).

Note

Network appliances, such as VPN Gateway and Application Gateway that run inside a virtual network, come with additional cost. To learn more, see [Virtual Network pricing](https://azure.microsoft.com/pricing/details/virtual-network/).

If there is no existing Azure Virtual Network gateway, Windows Admin Center creates one for you. The setup process can take up to 25 minutes. After the Azure Network Adapter is created, you can start to access VMs in the virtual network directly from your server.

If you don’t need the connectivity anymore, under **Networks**, select the Azure Network Adapter that you want to disconnect, from the top menu, select **Disconnect**, and then on the **Disconnect VPN Confirmation** pop-up window, select **Yes**.