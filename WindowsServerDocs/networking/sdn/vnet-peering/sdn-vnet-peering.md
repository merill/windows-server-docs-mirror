---
layout: Conceptual
title: Virtual network peering | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/vnet-peering/sdn-vnet-peering
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: 'Learn more about: Virtual network peering'
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-11-04T00:00:00.0000000Z
locale: en-us
document_id: b4d9e1bc-c889-255c-6d4b-0178a18b2509
document_version_independent_id: 900d1a40-60ce-7225-64a9-11fd2d5e42c2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/vnet-peering/sdn-vnet-peering.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/vnet-peering/sdn-vnet-peering
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/vnet-peering/sdn-vnet-peering.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
platformId: 907dba19-2d12-ce6d-fa8d-fd8f6717b02c
---

# Virtual network peering | Microsoft Learn

Virtual network peering lets you connect two virtual networks seamlessly. Once peered, for connectivity purposes, the virtual networks appear as one.

The benefits of using virtual network peering include:

- Traffic between virtual machines in the peered virtual networks gets routed through the backbone infrastructure through *private* IP addresses only. The communication between the virtual networks does not require public Internet or gateways.
- A low-latency, high-bandwidth connection between resources in different virtual networks.
- The ability for resources in one virtual network to communicate with resources in a different virtual network.
- No downtime to resources in either virtual network when creating the peering.

## Requirements and constraints

Virtual network peering has a few requirements and constraints:

- Peered virtual networks must:

    - Have non-overlapping IP address spaces
    - Be managed by the same Network Controller
- Once you peer a virtual network with another virtual network, you cannot add or delete address ranges in the address space.

    Tip

    If you need to add address ranges:

    1. Remove the peering.
    2. Add the address space.
    3. Add the peering again.
- Since virtual network peering is between two virtual networks, there is no derived transitive relationship across peerings. For example, if you peer virtualNetworkA with virtualNetworkB and virtualNetworkB with virtualNetworkC, then virtualNetworkA does not get peered with virtualNetworkC.

## Connectivity

After you peer virtual networks, resources in either virtual network can directly connect with resources in the peered virtual network.

- Network latency between virtual machines in peered virtual networks is the same as the latency within a single virtual network.
- Network throughput is based on the bandwidth allowed for the virtual machine. There isn't any additional restriction on bandwidth within the peering.
- Traffic between virtual machines in peered virtual networks is routed directly through the backbone infrastructure, not through a gateway or over the public Internet.
- Virtual machines in a virtual network can access the internal load-balancer in the peered virtual network.

You can apply access control lists (ACLs) in either virtual network to block access to other virtual networks or subnets if desired. If you open full connectivity between peered virtual networks (which is the default option), you can apply ACLs to specific subnets or virtual machines to block or deny specific access. To learn more about ACLs, see [Use Access Control Lists (ACLs) to Manage Datacenter Network Traffic Flow](/en-us/azure/azure-local/manage/use-datacenter-firewall-powershell?context=/windows-server/context/windows-server-edge-networking).

## Service chaining

You can configure user-defined routes that point to virtual machines in peered virtual networks as the next hop IP address, to enable service chaining. Service chaining enables you to direct traffic from one virtual network to a virtual appliance, in a peered virtual network, through user-defined routes.

You can deploy hub-and-spoke networks, where the hub virtual network can host infrastructure components such as a network virtual appliance. All the spoke virtual networks peer with the hub virtual network. Traffic can flow through network virtual appliances in the hub virtual network.

Virtual network peering enables the next hop in a user-defined route to be the IP address of a virtual machine in the peered virtual network. To learn more about user-defined routes, see [Use Network Virtual Appliances on a Virtual Network](../manage/use-network-virtual-appliances-on-a-vn).

## Gateways and on-premises connectivity

Each virtual network, regardless of whether peered with another virtual network, can still have its own gateway to connect to an on-premises network. When you peer virtual networks, you can also configure the gateway in the peered virtual network as a transit point to an on-premises network. In this case, the virtual network that uses a remote gateway cannot have its own gateway. A virtual network can have only one gateway that can be either a local or remote gateway (in the peered virtual network).

## Monitor

When you peer two virtual networks, you must configure a peering for each virtual network in the peering.

You can monitor the status of your peering connection, which can be in one of the following states:

- **Initiated:** Shown when you create the peering from the first virtual network to the second virtual network.
- **Connected:** Shown after you've created the peering from the second virtual network to the first virtual network. The peering state for the first virtual network changes from Initiated to Connected. Both virtual network peers must have the state of Connected before establishing a virtual network peering successfully.
- **Disconnected:** Shown if one virtual network disconnects from another virtual network.

[infographic of the states]