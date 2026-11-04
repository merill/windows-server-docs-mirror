---
layout: Conceptual
title: Network Function Virtualization | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/technologies/network-function-virtualization/network-function-virtualization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: You can use this topic to learn about Network Function Virtualization, which allows you to deploy virtual networking appliances like Datacenter Firewall, multitenant RAS Gateway, and Software Load Balancing (SLB) in Windows Server 2019 and 2016.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-28T00:00:00.0000000Z
locale: en-us
document_id: 50476477-7373-efd2-47ba-a6e0c0f3aabb
document_version_independent_id: 046f305f-5aba-e5ff-18b7-3640af7aad82
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/technologies/network-function-virtualization/Network-Function-Virtualization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/technologies/network-function-virtualization/network-function-virtualization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/technologies/network-function-virtualization/Network-Function-Virtualization.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f1e0857d-d76b-e3c1-d3a9-3d40520be6a1
---

# Network Function Virtualization | Microsoft Learn

You can use this topic to learn about Network Function Virtualization, which allows you to deploy virtual networking appliances such as Datacenter Firewall, multitenant RAS Gateway, and Software Load Balancing (SLB) multiplexer (MUX).

Note

In addition to this topic, the following Network Function Virtualization documentation is available.

- [Datacenter Firewall Overview](/en-us/azure/azure-local/concepts/datacenter-firewall-overview?context=/windows-server/context/windows-server-edge-networking)
- [RAS Gateway for SDN](/en-us/azure/azure-local/concepts/gateway-overview?context=/windows-server/context/windows-server-edge-networking)
- [Software Load Balancing (SLB) for SDN](/en-us/azure/azure-local/concepts/software-load-balancer?context=/windows-server/context/windows-server-edge-networking)

In today's software defined datacenters, network functions that are being performed by hardware appliances (such as load balancers, firewalls, routers, switches, and so on) are increasingly being virtualized as virtual appliances. This "network function virtualization" is a natural progression of server virtualization and network virtualization. Virtual appliances are quickly emerging and creating a brand new market. They continue to generate interest and gain momentum in both virtualization platforms and cloud services.

Microsoft included a standalone gateway as a virtual appliance starting with Windows Server 2012 R2 . For more information, see [Windows Server Gateway](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn313101%28v=ws.11%29). Now with Windows Server 2016 Microsoft continues to expand and invest in the network function virtualization market.

## Virtual appliance benefits

A virtual appliance is dynamic and easy to change because it is a pre-built, customized virtual machine. It can be one or more virtual machines packaged, updated, and maintained as a unit. Together with software defined networking (SDN), you get the agility and flexibility needed in today's cloud-based infrastructure. For example:

- SDN presents the network as a pooled and dynamic resource.
- SDN facilitates tenant isolation.
- SDN maximizes scale and performance.
- Virtual appliances enable seamless capacity expansion and workload mobility.
- Virtual appliances minimize operational complexity.
- Virtual appliances let customers easily acquire, deploy, and manage pre-integrated solutions.

    - Customers can easily move the virtual appliance anywhere in the cloud.
    - Customers can scale virtual appliances up or down dynamically based on demand.

For more information about Microsoft SDN see [Software Defined Networking](../../software-defined-networking).

### What network functions are being virtualized?

The marketplace for virtualized network functions is growing quickly. The following network functions are being virtualized:

- **Security**

    - Firewall
    - Antivirus
    - DDoS (Distributed Denial of Service)
    - IPS/IDS (Intrusion Prevention System/Intrusion Detection System)
- **Application/WAN optimizers**
- **Edge**

    - Site-to-site gateway
    - L3 gateways
    - Routers
    - Switches
    - NAT
    - Load balancers (not necessarily at the edge)
    - HTTP proxy

## Why Microsoft is a great platform for virtual appliances

![Virtual network stack](../../../media/network-function-virtualization/microsoft-network-function-virtualization.png)

The Microsoft platform has been engineered to be a great platform to build and deploy virtual appliances. Here's why:

- Microsoft provides key virtualized network functions with Windows Server 2016.
- You can deploy a virtual appliance from the vendor of your choice.
- You can deploy, configure, and manage your virtual appliances with the Microsoft Network Controller which comes with Windows Server 2016. For more information about the Network Controller, see [Network Controller](/en-us/azure/azure-local/concepts/network-controller-overview?context=/windows-server/context/windows-server-edge-networking).
- Hyper-V can host the top guest operating systems that you need.

## Network function virtualization in Windows Server 2016

### Virtual appliances functions provided by Microsoft

The following virtual appliances are provided with Windows Server 2016:

**Software load balancer**

A layer-4 load balancer operating at datacenter scale. This is a similar version of Azure's load balancer that has been deployed at scale in the Azure environment. For more information about the Microsoft Software Load Balancer, see [Software Load Balancing (SLB) for SDN](/en-us/previous-versions/windows/server/mt632286%28v=ws.12%29). For more information about Microsoft Azure Load Balancing Services, see [Microsoft Azure Load Balancing Services](https://azure.microsoft.com/blog/microsoft-azure-load-balancing-services/).

**Gateway**. RAS Gateway provides all combinations of the following gateway functions.

- **Site-to-Site gateway**

    RAS Gateway provides a Border Gateway Protocol (BGP)-capable, multitenant gateway that allows your tenants to access and manage their resources over site-to-site VPN connections from remote sites, and that allows network traffic flow between virtual resources in the cloud and tenant physical networks. For more information about the RAS Gateway, see [RAS Gateway High Availability](/en-us/previous-versions/windows/server/mt631692%28v=ws.12%29) and [RAS Gateway](../../../../remote/remote-access/ras-gateway/ras-gateway).
- **Forwarding gateway**

    RAS Gateway routes traffic between virtual networks and the hosting provider physical network. For example, if tenants create one or more virtual networks, and need access to shared resources on the physical network at the hosting provider, the forwarding gateway can route traffic between the virtual network and the physical network to provide users working on the virtual network with the services that they need. For more information, see [RAS Gateway High Availability](/en-us/previous-versions/windows/server/mt631692%28v=ws.12%29) and [RAS Gateway](../../../../remote/remote-access/ras-gateway/ras-gateway).
- **GRE tunnel gateways**

    GRE based tunnels enable connectivity between tenant virtual networks and external networks. Since the GRE protocol is lightweight and support for GRE is available on most network devices, it becomes an ideal choice for tunneling where data encryption is not required. GRE support in Site to Site (S2S) tunnels solves the problem of forwarding between tenant virtual networks and tenant external networks using a multi-tenant gateway. For more information about GRE tunnels, see [GRE Tunneling in Windows Server 2016](../../../../remote/remote-access/ras-gateway/gre-tunneling-windows-server).

**Routing control plane with BGP**

Hyper-V Network Virtualization (HNV) Routing Control is the logical, centralized entity in the control plane, which carries all the Customer Address plane routes and dynamically learns and then updates the distributed RAS Gateway routers in the virtual network. For more information, see [RAS Gateway High Availability](/en-us/previous-versions/windows/server/mt631692%28v=ws.12%29) and [RAS Gateway](../../../../remote/remote-access/ras-gateway/ras-gateway).

**Distributed multi-tenant firewall**

The firewall protects the network layer of virtual networks. The policies are enforced at the SDN-vSwitch port of each tenant VM. It protects all traffic flows: east-west and north-south. The policies are pushed through the tenant portal and the Network Controller distributes them to all applicable hosts. For more information about the distributed multi-tenant firewall, see [Datacenter Firewall Overview](/en-us/azure/azure-local/concepts/datacenter-firewall-overview?context=/windows-server/context/windows-server-edge-networking).