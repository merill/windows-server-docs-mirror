---
layout: Conceptual
title: Understand the usage of virtual networks and VLANs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/manage/understanding-usage-of-virtual-networks-and-vlans
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: In this topic, you learn about Hyper-V network virtualization virtual networks and how they differ from virtual local area networks (VLANs). With Hyper-V network virtualization, you create overlay virtual networks, also called virtual networks.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-28T00:00:00.0000000Z
locale: en-us
document_id: be9b2241-6051-a092-490e-876ba69a2e8a
document_version_independent_id: 04081583-f813-5df7-3e2b-0426dc7cbd37
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/manage/Understanding-Usage-of-Virtual-Networks-and-VLANs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/manage/understanding-usage-of-virtual-networks-and-vlans
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/manage/Understanding-Usage-of-Virtual-Networks-and-VLANs.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
platformId: aaab077b-c06d-d8c3-e0f5-a1c9b971078f
---

# Understand the usage of virtual networks and VLANs | Microsoft Learn

In this topic, you learn about Hyper-V network virtualization virtual networks and how they differ from virtual local area networks (VLANs). With Hyper-V network virtualization, you create overlay virtual networks, also called virtual networks.

Software Defined Networking (SDN) in Windows Server 2016 is based on programming policy for overlay virtual networks within a Hyper-V Virtual Switch. You can create overlay virtual networks, also called Virtual Networks, with Hyper-V Network Virtualization.

When you deploy Hyper-V Network Virtualization, overlay networks are created by encapsulating the original tenant virtual machine's Layer-2 Ethernet frame with an overlay - or tunnel - header (for example, VXLAN or NVGRE) and Layer-3 IP and Layer-2 Ethernet headers from the underlay (or physical) network. The overlay virtual networks are identified by a 24-bit Virtual Network Identifier (VNI) to maintain tenant traffic isolation and to allow overlapping IP addresses. The VNI is composed of a virtual subnet ID (VSID), logical switch ID, and tunnel ID.

Additionally, each tenant is assigned a routing domain (similar to virtual routing and forwarding - VRF) so that multiple virtual subnet prefixes (each represented by a VNI) can be directly routed to each other. Cross-tenant (or cross routing domain) routing is not supported without going through a gateway.

The physical network on which each tenant's encapsulated traffic is tunneled is represented by a logical network called the provider logical network. This provider logical network consists of one or more subnets, each represented by an IP Prefix and, optionally, a VLAN 802.1q tag.

You can create additional logical networks and subnets for infrastructure purposes to carry management traffic, storage traffic, live migration traffic, etc.

Microsoft SDN does not support the isolation of tenant networks by using VLANs. Tenant isolation is accomplished solely by using Hyper-V Network Virtualization overlay Virtual Networks and encapsulation.