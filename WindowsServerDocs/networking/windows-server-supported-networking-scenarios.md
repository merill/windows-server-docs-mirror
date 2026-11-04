---
layout: Conceptual
title: Windows Server supported networking scenarios | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/windows-server-supported-networking-scenarios
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides information about new supported Networking scenarios in Windows Server 2016 and later
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: c7a8019c-3466-91ef-618f-ef99cf29eceb
document_version_independent_id: 60290b39-1999-86be-2030-30618f5c003e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/windows-server-supported-networking-scenarios.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/windows-server-supported-networking-scenarios
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/windows-server-supported-networking-scenarios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
platformId: efb14aa3-ecd1-43a5-7bf6-456eb89f3426
---

# Windows Server supported networking scenarios | Microsoft Learn

This topic provides information about supported and unsupported scenarios that you can or cannot perform with this release of Windows Server 2016.

Important

For all production scenarios, use the latest signed hardware drivers from your original equipment manufacturer (OEM) or independent hardware vendor (IHV).

## Supported Networking Scenarios

This section includes information about the supported networking scenarios for Windows Server 2016, and includes the following scenario categories.

- Software Defined Networking (SDN) scenarios
- Network Platform scenarios
- DNS Server scenarios
- IPAM scenarios with DHCP and DNS
- NIC Teaming scenarios
- Switch Embedded Teaming (SET) scenarios

### Software Defined Networking (SDN) scenarios

You can use the following documentation to deploy SDN scenarios with Windows Server 2016.

- [Deploy a Software Defined Network infrastructure using scripts](sdn/deploy/deploy-a-software-defined-network-infrastructure-using-scripts)

For more information, see [Software Defined Networking (SDN)](/en-us/azure/azure-local/concepts/software-defined-networking?context=/windows-server/context/windows-server-edge-networking).

#### Network Controller scenarios

The Network Controller scenarios allow you to:

- Deploy and manage a multiple-node instance of Network Controller. For more information, see [Deploy Network Controller using Windows PowerShell](sdn/deploy/deploy-network-controller-using-windows-powershell).
- Use Network Controller to programmatically define network policy by using the REST Northbound API.
- Use Network Controller to create and manage virtual networks with Hyper-V Network Virtualization - using NVGRE or VXLAN encapsulation.

For more information, see [Network Controller](/en-us/azure/azure-local/concepts/network-controller-overview?context=/windows-server/context/windows-server-edge-networking).

#### Network Function Virtualization (NFV) scenarios

The NFV scenarios allow you to:

- Deploy and use a software load balancer to distribute both northbound and southbound traffic.
- Deploy and use a software load balancer to distribute eastbound and westbound traffic for virtual networks created with Hyper-V Network Virtualization.
- Deploy and use a NAT software load balancer for virtual networks created with Hyper-V Network Virtualization.
- Deploy and use a Layer 3 forwarding gateway
- Deploy and use a virtual private network (VPN) gateway for site-to-site IPsec (IKEv2) tunnels
- Deploy and use a Generic Routing Encapsulation (GRE) gateway.
- Deploy and configure dynamic routing and transit routing between sites using Border Gateway Protocol (BGP).
- Configure M+N redundancy for Layer 3 and site-to-site gateways, and for BGP routing.
- Use Network Controller to specify ACLs on virtual networks and network interfaces.

For more information, see [Network Function Virtualization](sdn/technologies/network-function-virtualization/network-function-virtualization).

### Network Platform scenarios

For the scenarios in this section the Windows Server Networking team supports the use of any Windows Server 2016 certified driver. Please check with your network interface card (NIC) manufacturer to ensure you have the most recent driver updates.

The network platform scenarios allow you to:

- Use a converged NIC to combine both RDMA and Ethernet traffic using a single network adapter.
- Create a low-latency data path by using Packet Direct, enabled in the Hyper-V Virtual Switch, and a single network adapter.
- Configure SET to spread SMB Direct and RDMA traffic flows between up to two network adapters.

For more information, see [Remote Direct Memory Access (RDMA) and Switch Embedded Teaming (SET)](/en-us/azure/azure-local/concepts/host-network-requirements?context=/windows-server/context/windows-server-edge-networking).

#### Hyper-V Virtual Switch Scenarios

The Hyper-V Virtual Switch scenarios allow you to:

- Create a Hyper-V Virtual Switch with a Remote Direct Memory Access (RDMA) vNIC
- Create a Hyper-V Virtual Switch with Switch Embedded Teaming (SET) and RDMA vNICs
- Create a SET team in Hyper-V Virtual Switch
- Manage a SET team by using Windows PowerShell commands

For more information, see [Remote Direct Memory Access (RDMA) and Switch Embedded Teaming (SET)](/en-us/azure/azure-local/concepts/host-network-requirements?context=/windows-server/context/windows-server-edge-networking)

### DNS Server scenarios

DNS Server scenarios allow you to:

- Specify Geo-Location based traffic management using DNS Policies
- Configure split-brain DNS using DNS Policies
- Apply filters on DNS queries using DNS Policies
- Configure Application Load Balancing using DNS Policies
- Specify Intelligent DNS Responses based on the time of day
- Configure DNS Zone transfer policies
- Configure DNS server policies on Active Directory Domain Services (AD DS) integrated zones
- Configure Response Rate Limiting
- Specify DNS-based Authentication of Named Entities (DANE)
- Configure support for Unknown Records in DNS

For more information, see the topics [What's New in DNS Client in Windows Server 2016](dns/what-s-new-in-dns-client) and [What's New in DNS Server in Windows Server 2016](dns/what-s-new-in-dns-server).

### IPAM scenarios with DHCP and DNS

The IPAM scenarios allow you to:

- Discover and administer DNS and DHCP servers and IP addressing across multiple federated Active Directory forests
- Use IPAM for centralized management of DNS properties, including zones and resource records.
- Define granular role-based access control policies and delegate IPAM users or user groups to manage the set of DNS properties that you specify.
- Use the Windows PowerShell commands for IPAM to automate access control configuration for DHCP and DNS.

    For more information, see [Manage IPAM](technologies/ipam/manage-ipam).

### NIC Teaming scenarios

The NIC Teaming scenarios allow you to:

- Create a NIC team in a supported configuration
- Delete a NIC team
- Add network adapters to the NIC team in a supported configuration
- Remove network adapters from the NIC team

Note

In Windows Server 2016, you can use NIC Teaming in Hyper-V, however in some cases Virtual Machine Queues (VMQ) might not automatically enable on the underlying network adapters when you create a NIC Team. If this occurs, you can use the following Windows PowerShell command to ensure that VMQ is enabled on the NIC team member adapters: `Set-NetAdapterVmq -Name <NetworkAdapterName> -Enable`

### Switch Embedded Teaming (SET) scenarios

SET is an alternative NIC Teaming solution that you can use in environments that include Hyper-V and the Software Defined Networking (SDN) stack in Windows Server 2016. SET integrates some NIC Teaming functionality into the Hyper-V Virtual Switch.

For more information, see [Remote Direct Memory Access (RDMA) and Switch Embedded Teaming (SET)](/en-us/azure/azure-local/concepts/host-network-requirements?context=/windows-server/context/windows-server-edge-networking)

## Unsupported Networking Scenarios

The following networking scenarios are not supported in Windows Server 2016.

- VLAN-based tenant virtual networks.
- IPv6 is not supported in either the underlay or overlay.