---
layout: Conceptual
title: SDN Technologies | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/technologies/software-defined-networking-technologies
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: The topics in this section provide overview and technical information about the Software Defined Networking technologies that are included in Windows Server 2019 and 2016.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-27T00:00:00.0000000Z
locale: en-us
document_id: 811f1556-5af4-6157-dfc7-560da82b4e30
document_version_independent_id: a93d63c1-e1c7-0203-d4e5-151418bd01e1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/technologies/Software-Defined-Networking-Technologies.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/technologies/software-defined-networking-technologies
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/technologies/Software-Defined-Networking-Technologies.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: 73fad3b8-fd90-c8e0-78e1-d7fe648f13f0
---

# SDN Technologies | Microsoft Learn

The topics in this section provide overview and technical information about the Software Defined Networking technologies that are included in Windows Server.

## [Network Controller](/en-us/azure/azure-local/concepts/network-controller-overview?context=/windows-server/context/windows-server-edge-networking)

The network controller provides a centralized, programmable point of automation to manage, configure, monitor, and troubleshoot both virtual and physical network infrastructure in your datacenter. With the network controller, you can automate the configuration of network infrastructure instead of performing manual configuration of network devices and services.

The network controller is a highly available and scalable server and provides two application programming interfaces (APIs):

1. **Southbound API** – allows the network controller to communicate with the network.
2. **Northbound API** – allows you to communicate with the network controller.

You can use Windows PowerShell, the Representational State Transfer (REST) API, or a management application to manage the following physical and virtual network infrastructure:

- Hyper-V VMs and virtual switches
- Physical network switches
- Physical network routers
- Firewall software
- VPN Gateways, including Remote Access Service (RAS) Multitenant Gateways
- Load Balancers

## [Hyper-V Network Virtualization](hyper-v-network-virtualization/hyper-v-network-virtualization)

Hyper-V Network Virtualization (HNV) helps you abstract your applications and workloads from the physical network by using virtual networks. Virtual networks provide the necessary multitenant isolation while running on a shared physical network fabric, thereby driving up resource utilization. To ensure that you can carry forward your existing investments, you can set up virtual networks on existing networking gear. Also, virtual networks are compatible with virtual Local Area Networks (VLANs).

## [Hyper-V Virtual Switch](../../../virtualization/hyper-v/virtual-switch)

The Hyper-V Virtual Switch is a software-based layer-2 Ethernet network switch that is available in Hyper-V Manager after you have installed the Hyper-V server role. The switch includes programmatically managed and extensible capabilities to connect virtual machines to both virtual networks and the physical network. Also, Hyper-V Virtual Switch provides policy enforcement for security, isolation, and service levels.

You can also deploy the Hyper-V Virtual Switch with Switch Embedded Teaming (SET) and Remote Direct Memory Access (RDMA). For more information, see the section Remote Direct Memory Access (RDMA) and Switch Embedded Teaming (SET) in this topic.

## [Internal DNS Service (iDNS) for SDN](idns-for-sdn)

Hosted virtual machines (VMs) and applications require DNS to communicate within their networks and with external resources on the Internet. With iDNS, you can provide tenants with DNS name resolution services for isolated, local namespace and Internet resources.

## [Network Function Virtualization](network-function-virtualization/network-function-virtualization)

Hardware appliances, such as load balancers, firewalls, routers, and switches are increasingly becoming virtual appliances. Microsoft has virtualized networks, switches, gateways, NATs, load balancers, and firewalls. This "network function virtualization" is a natural progression of server virtualization and network virtualization. Virtual appliances are quickly emerging and creating a brand new market. They continue to generate interest and gain momentum in both virtualization platforms and cloud services.

The following Network Function Virtualization technologies are available.

- **Software Load Balancer (SLB) and Network Address Translation (NAT)**. Enhance throughput by supporting Direct Server Return in which the return network traffic can bypass the Load Balancing multiplexer. For more details, see [Software Load Balancing /(SLB/) for SDN](/en-us/azure/azure-local/concepts/software-load-balancer?context=/windows-server/context/windows-server-edge-networking).
- **Datacenter Firewall**. Provide granular access control lists (ACLs), enabling you to apply firewall policies at the VM interface level or the subnet level. For more details, see [Datacenter Firewall Overview](/en-us/azure/azure-local/concepts/datacenter-firewall-overview?context=/windows-server/context/windows-server-edge-networking).
- **RAS Gateway for SDN**. Route network traffic between the physical network and VM network resources, regardless of the location. You can route the network traffic at the same physical location or many different locations. For more details, see [RAS Gateway for SDN](/en-us/azure/azure-local/concepts/gateway-overview?context=/windows-server/context/windows-server-edge-networking).

## Remote Direct Memory Access (RDMA) and Switch Embedded Teaming (SET)

In Windows Server 2016, you can enable RDMA on network adapters that are bound to a Hyper-V Virtual Switch with or without Switch Embedded Teaming (SET). This allows you to use fewer network adapters when you want to use RDMA and SET at the same time.

SET is an alternative NIC Teaming solution that you can use in environments that include Hyper-V and the Software Defined Networking (SDN) stack in Windows Server 2016. SET integrates some of the NIC Teaming functionality into the Hyper-V Virtual Switch.

SET allows you to group between one and eight physical Ethernet network adapters into one or more software-based virtual network adapters. These virtual network adapters provide fast performance and fault tolerance in the event of a network adapter failure. SET member network adapters must all be installed in the same physical Hyper-V host to be placed in a team.

In addition, you can use Windows PowerShell commands to enable Data Center Bridging (DCB), create a Hyper-V Virtual Switch with an RDMA virtual NIC (vNIC), and create a Hyper-V Virtual Switch with SET and RDMA vNICs. For more information, see [Remote Direct Memory Access (RDMA) and Switch Embedded Teaming (SET)](/en-us/azure/azure-local/concepts/host-network-requirements?context=/windows-server/context/windows-server-edge-networking).

## [Border Gateway Protocol (BGP)](../../../remote/remote-access/bgp/border-gateway-protocol-bgp)

Border Gateway Protocol (BGP) is a dynamic routing protocol that automatically learns routes between sites that use site-to-site VPN connections. Therefore, BGP reduces manual configuration of routers. When you configure RAS Gateway, BGP lets you manage the routing of network traffic between your tenants' VM networks and remote sites.

## [Software Load Balancing (SLB) for SDN](/en-us/azure/azure-local/concepts/software-load-balancer?context=/windows-server/context/windows-server-edge-networking)

Cloud Service Providers (CSPs) and Enterprises that deploy SDN can use Software Load Balancing (SLB) to evenly distribute tenant and tenant customer network traffic among virtual network resources. The Windows Server SLB enables multiple servers to host the same workload, providing high availability and scalability.

## [Windows Server Containers](containers/container-networking-overview)

Windows Server Containers are a lightweight operating system virtualization method separating applications or services from other services running on the same container host. Each container has its own operating system, processes, file system, registry, and IP addresses, which you can connect to virtual networks.

## System Center

Deploy and manage the SDN infrastructure with [Virtual Machine Management (VMM)](/en-us/system-center/vmm/) and [Operations Manager](/en-us/system-center/scom/). With VMM, you provision and manage the resources needed to create and deploy virtual machines and services to private clouds. With Operations Manager, you monitor services, devices, and operations across your enterprise to identify problems for immediate action.