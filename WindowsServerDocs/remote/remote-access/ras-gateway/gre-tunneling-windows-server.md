---
layout: Conceptual
title: GRE Tunneling in Windows Server 2016 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras-gateway/gre-tunneling-windows-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: You can use this topic to gain an understanding of updates to Generic Routing Encapsulation (GRE) tunnel capability for RAS Gateway in Windows Server 2016.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 6b51f141-c940-4ab2-b049-2b8682623e67
document_version_independent_id: 889ed2ba-de9a-a432-3698-26f3831748d4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras-gateway/gre-tunneling-windows-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras-gateway/gre-tunneling-windows-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras-gateway/gre-tunneling-windows-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d5b80bab-80ab-c6f1-77ae-d4e39d34cfd5
---

# GRE Tunneling in Windows Server 2016 | Microsoft Learn

Windows Server 2016 provides updates to Generic Routing Encapsulation (GRE) tunnel capability for the RAS Gateway.

GRE is a lightweight tunneling protocol that can encapsulate a wide variety of network layer protocols inside virtual point-to-point links over an Internet Protocol internetwork. The Microsoft GRE implementation can encapsulate IPv4 and IPv6.

GRE tunnels are useful in many scenarios because:

- They are lightweight and RFC 2890 compliant, making it interoperable with various vendor devices
- You can use Border Gateway Protocol (BGP) for dynamic routing
- You can configure GRE multitenant RAS Gateways for use with Software Defined Networking (SDN)
- You can use System Center Virtual Machine Manager to manage GRE-based RAS Gateways
- You can achieve up to 2.0 Gbps throughput on a 6 core virtual machine that is configured as a GRE RAS Gateway
- A single gateway supports multiple connection modes

GRE based tunnels enable connectivity between tenant virtual networks and external networks. Since the GRE protocol is lightweight and support for GRE is available on most of network devices it becomes an ideal choice for tunneling where the encryption of data is not required.

GRE support in Site to Site (S2S) tunnels solves the problem of forwarding between tenant virtual networks and tenant external networks using a multi-tenant gateway, as described later in this topic.

The GRE tunnel feature is designed to address the following requirements:

- A hosting provider must be able to create virtual networks for forwarding without modifying the physical switch configuration.
- A hosting provider must be able to add subnets to their externally facing networks without modifying the configuration of the physical switches within their infrastructure. The GRE tunnel feature enables or enhances several key scenarios for hosting service providers using Microsoft technologies to implement Software Defined Networking in their service offerings.

The following are some example scenarios:

- Access from tenant virtual networks to tenant physical networks
- High speed connectivity
- Integration with VLAN based isolation
- Access shared resources
- Services of third party devices to tenants

## Key scenarios

The following are key scenarios that the GRE tunnel feature addresses.

### Access from tenant virtual networks to tenant physical networks

This scenario enables a scalable way to provide access from tenant virtual networks to tenant physical networks located on the hosting service provider premises. A GRE tunnel endpoint is established on the multitenant gateway, the other GRE tunnel endpoint is established on a third-party device on the physical network. Layer-3 traffic is routed between the virtual machines in the virtual network and the third-party device on the physical network.

![GRE tunnel connecting hoster physical network and tenant virtual network](../../media/gre-tunneling-in-windows-server/gre_.png)

### High speed connectivity

This scenario enables a scalable way to provide high speed connectivity from the tenant on-premises network to their virtual network located in the hosting service provider network. A tenant connects to the service provider network via multiprotocol label switching (MPLS), where a GRE tunnel is established between the hosting service provider's edge router and the multitenant gateway to the tenant's virtual network.

![GRE tunnel connecting tenant enterprise MPLS network and tenant virtual network](../../media/gre-tunneling-in-windows-server/gre-.png)

### Integration with VLAN based isolation

This scenario allows you to integrate VLAN based isolation with Hyper-V Network Virtualization. A physical network on the hosting provider network contains a load balancer using VLAN-based isolation. A multitenant gateway establishes GRE tunnels between the load balancer on the physical network and the multitenant gateway on the virtual network.

Multiple tunnels can be established between the source and destination, and the GRE key is used to discriminate between the tunnels.

![Multiple GRE tunnels connecting tenant virtual networks](../../media/gre-tunneling-in-windows-server/gre-vlanisolation.png)

### Access shared resources

This scenario allows you to access shared resources on a physical network located on the hosting provider network.

You may have a shared service located on a server on a physical network located in the hosting provider network that you want to share with multiple tenant virtual networks.

The tenant networks with non-overlapping subnets access the common network over a GRE tunnel. A single tenant gateway routes between the GRE tunnels, thus routing packets to the appropriate tenant networks.

In this scenario, the single tenant gateway can be replaced by third-party hardware appliances.

![A single-tenant gateway using multiple tunnels to connect multiple virtual networks](../../media/gre-tunneling-in-windows-server/gre-sharedresource.png)

### Services of third party devices to tenants

This scenario can be used to integrate third party devices (such as hardware load balancers) into the tenant virtual network traffic flow. For example, traffic originating from an enterprise site passes through a S2S tunnel to the multitenant gateway. The traffic is routed to the load balancer over a GRE tunnel. The load balancer routes traffic to multiple virtual machines on the enterprise's virtual network. The same thing happens for another tenant with potentially overlapping IP addresses in the virtual networks. The network traffic is isolated on the load balancer using VLANs, and is applicable to all layer 3 devices that support VLANs.

![Multiple GRE tunnels connecting virtual networks to third-party devices](../../media/gre-tunneling-in-windows-server/grethirdparty.png)

## Configuration and deployment

A GRE tunnel is exposed as an additional protocol within a S2S interface. It is implemented in a similar fashion as an IPSec S2S tunnel described in the following Networking Blog: [Multi-tenant Site-to-Site (S2S) VPN Gateway with Windows Server 2012 R2](https://techcommunity.microsoft.com/t5/networking-blog/bg-p/NetworkingBlog)

See the following topic for an example that deploys gateways, including GRE tunnel gateways:

[Deploy a Software Defined Network infrastructure using scripts](../../../networking/sdn/deploy/deploy-a-software-defined-network-infrastructure-using-scripts)

## More information

For more information about deploying S2S gateways, see the following topics:

- [RAS Gateway](ras-gateway)
- [Border Gateway Protocol (BGP)](../bgp/border-gateway-protocol-bgp)
- [New! Windows Server 2012 R2 RAS Multitenant Gateway Deployment Guide](https://techcommunity.microsoft.com/t5/networking-blog/bg-p/NetworkingBlog)
- [Deploy Border Gateway Protocol (BGP) with the RAS Multitenant Gateway](https://techcommunity.microsoft.com/t5/networking-blog/bg-p/NetworkingBlog)