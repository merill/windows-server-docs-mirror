---
layout: Conceptual
title: RAS Gateway GRE Tunnel Throughput and Performance | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras-gateway/ras-gateway-gre-perf
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: This topic, which is intended for Information Technology (IT) professionals, provides throughput performance information about RAS Gateway Generic Routing Encapsulation (GRE) tunnels.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 5d67b2b0-afe0-6b7d-6a84-97b87c626681
document_version_independent_id: 79ded197-1a61-1ac0-8775-4d5b01ec4e16
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras-gateway/RAS-Gateway-GRE-Perf.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras-gateway/ras-gateway-gre-perf
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras-gateway/RAS-Gateway-GRE-Perf.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
platformId: 37aee596-9565-68a8-7aec-7822ec65e166
---

# RAS Gateway GRE Tunnel Throughput and Performance | Microsoft Learn

You can use this topic to learn about Remote Access Server (RAS) Gateway Generic Routing Encapsulation (GRE) Tunnel performance on Windows Server, version 1709, in a non-Software Defined Networking (SDN) based test environment.

RAS Gateway is a software router and gateway that you can use in either single tenant mode or multitenant mode. This topic discusses a single tenant mode, high availability configuration with Failover Clustering. The GRE tunnel performance statistics that are presented in this topic are valid for RAS Gateway in both single tenant and multitenant modes.

Note

Failover Clustering is a Windows Server feature that enables you to group multiple servers together into a fault-tolerant cluster. For more information, see [Failover Clustering](../../../failover-clustering/failover-clustering-overview)

Single tenant mode allows organizations of any size to deploy the gateway as an exterior, or Internet-facing edge virtual private network (VPN) server. In single tenant mode, you can deploy RAS Gateway on a physical server or virtual machine (VM). This topic describes RAS Gateway deployment on two Virtual Machines (VMs) that are configured in a failover cluster.

Important

Because GRE tunnels provide encapsulation but not encryption, you should not use RAS Gateway configured with GRE as an Internet edge gateway. To learn about the best uses for RAS Gateway with GRE tunnels, see [GRE Tunneling in Windows Server](gre-tunneling-windows-server).

GRE is a lightweight tunneling protocol that can encapsulate a wide variety of network layer protocols inside virtual point-to-point links over an Internet Protocol internetwork. The Microsoft GRE implementation encapsulates both IPv4 and IPv6.

For more information, see the section **RAS Gateway Deployment Scenarios** in the topic [RAS Gateway](ras-gateway#bkmk_deploy).

In this test scenario, which is depicted in the following illustration, the traffic flow that is measured moves from the Organization Intranet 2 out to the Organization Intranet 1. Tenant Workload VMs send network traffic from Intranet 2 to Intranet 1 by using RAS Gateway.

![RAS Gateway GRE tunnel test scenario overview](../../media/gre-tunnel-perf/gre-infrastructure.jpg)

## Test Environment Configuration

This section provides information about the test environment and RAS Gateway configuration.

In the test environment, RAS Gateway VMs are deployed on Hyper-V hosts in a failover cluster for high availability.

### Hyper-V Host Configuration

Two Hyper-V hosts are configured to support the test scenario in the following manner.

- Two dual-homed physical computers are configured with Windows Server, version 1709
- The two physical network adapters in each of the two servers are connected to different subnetworks - both of which represent subnets of an Organization Intranet. Both networks and supporting hardware have a capacity of 10 GBps.
- Hyperthreading on the physical servers is disabled. This provides the maximum throughput from the physical NICs.
- The Hyper-V server role is installed on both servers and configured with two External Hyper-V Virtual Switches, one for each physical network adapter.
- Because both servers are connected to the same intranet, the servers can communicate with each other.
- The Hyper-V hosts are configured in a failover cluster over the intranet network.

Note

For more information, see [Hyper-V Virtual Switch](../../../virtualization/hyper-v/virtual-switch).

### VM Configuration

Two VMs are configured to support the test scenario in the following manner.

- On each server a VM is installed that is running Windows Server, version 1709. Each VM is configured with 10 Cores and 8 GB RAM.
- Each VM is also configured with two virtual network adapters. One virtual network adapter is connected to the Intranet 1 virtual switch, and the other virtual network adapter is connected to the Intranet 2 virtual switch.
- Each VM has RAS Gateway installed and configured as a GRE-based VPN server.
- The gateway VMs are configured in a failover cluster. When clustered, one VM is active and the other VM is passive.

### Workload Hyper-V Hosts and VMs

For this test, two Workload Hyper-V hosts are installed on the intranet, and each host has one VM installed. If you are duplicating this test in your own test environment, you can install as many workload servers and VMs as is appropriate for your purposes.

- Workload Hyper-V hosts have one physical network adapter installed that is connected to the Organization Intranet.
- In Hyper-V Virtual Switch, one virtual switch is created on each host. The switch is External and is bound to the one network adapter connected to the intranet.
- The workload VMs are configured with 2 GB RAM and 2 Cores.
- The Workload VMs each have one virtual network adapter that is connected to the intranet virtual switch.

### Traffic Generator Tool

The traffic generator tool that is used in this test is the ctsTraffic tool. The Git repository for this tool is located at https://github.com/Microsoft/ctsTraffic.

## RAS Gateway Performance

The illustrations in this section depict Task Manager displays of GRE tunnel throughput with multiple TCP connections.

You can achieve up to 2.0 Gbps throughput on multi-core VMs that are configured as GRE RAS Gateways.

### GRE Tunnel Performance with Multiple TCP Sessions

With multiple TCP sessions, the CPU utilization reaches 100% and the maximum throughput on the GRE tunnel is 2.0 Gbps.

The following illustration depicts CPU Utilization on both of the RAS Gateway VMs. The active VM, RAS Gateway VM #1, is on the left, while the passive VM, RAS Gateway VM #2, is on the right.

![Screenshot of two Task Manager windows showing CPU Utilization on both of the RAS Gateway VMs when there are multiple TCP sessions.](../../media/gre-tunnel-perf/gre-tunnel-01.jpg)

The following illustration depicts Ethernet network throughput on the RAS Gateway VMs. The active VM, RAS Gateway VM #1, is on the left, while the passive VM, RAS Gateway VM #2, is on the right.

![Screenshot of two Task Manager windows showing the Ethernet network throughput on the RAS Gateway VMs when there are multiple TCP sessions.](../../media/gre-tunnel-perf/gre-tunnel-02.jpg)

### GRE Tunnel Performance with One TCP Connection

With the test configuration changed from multiple TCP sessions to a single TCP session, only one CPU core reaches maximum capacity on the RAS Gateway VMs.

The maximum throughput on the GRE tunnel is between 400-500 Mbps.

The following illustration depicts CPU Utilization on both of the RAS Gateway VMs. The active VM, RAS Gateway VM #1, is on the left, while the passive VM, RAS Gateway VM #2, is on the right.

![Screenshot of two Task Manager windows showing CPU Utilization on both of the RAS Gateway VMs when there is one TCP session.](../../media/gre-tunnel-perf/gre-tunnel-03.jpg)

The following illustration depicts Ethernet network throughput on the RAS Gateway VMs. The active VM, RAS Gateway VM #1, is on the left, while the passive VM, RAS Gateway VM #2, is on the right.

![Screenshot of two Task Manager windows showing the Ethernet network throughput on the RAS Gateway VMs when there is one TCP session.](../../media/gre-tunnel-perf/gre-tunnel-04.jpg)

For more information about RAS Gateway performance, see [HNV Gateway Performance Tuning in Software Defined Networks](../../../administration/performance-tuning/subsystem/software-defined-networking/hnv-gateway-performance).