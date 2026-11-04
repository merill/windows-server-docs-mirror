---
layout: Conceptual
title: Plan for Hyper-V networking in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/plan/plan-hyper-v-networking-in-windows-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Describes what's needed for basic networking in Windows Server Hyper-V and gives links to instructions.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2026-01-21T00:00:00.0000000Z
locale: en-us
document_id: 1a270c3a-96f5-a8f8-3f18-22c82f135acb
document_version_independent_id: 49b9dbb2-e08d-275a-96ac-2369e97e0988
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/plan/plan-hyper-v-networking-in-windows-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/plan/plan-hyper-v-networking-in-windows-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/plan/plan-hyper-v-networking-in-windows-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 4499898e-2c30-fd7b-738d-057bdd33c0f8
---

# Plan for Hyper-V networking in Windows Server | Microsoft Learn

This article covers what you need for basic networking in Hyper-V, including considerations for live migration and other server features.

## Hyper-V networking basics

Hyper-V networking uses a virtual switch and a virtual network adapter. The virtual switch connects to an Ethernet-based network, and the virtual network adapter connects to a port on the virtual switch, enabling a virtual machine to use the network. When you create a virtual machine and connect the virtual machine to a virtual switch, a virtual network adapter is automatically added. All virtual switches are part of the Hyper-V host, but each virtual network adapter belongs to only one virtual machine. For instructions, see [Create a virtual switch for Hyper-V virtual machines](../get-started/create-a-virtual-switch-for-hyper-v-virtual-machines).

The virtual switch is a software-based layer-2 Ethernet network switch. The virtual switch provides built-in features for monitoring, controlling, and segmenting traffic, as well as security, and diagnostics. You can add to the set of built-in features by installing plug-ins, also called *extensions*. Extensions are available from independent software vendors. For more information about the switch and extensions, see [Hyper-V Virtual Switch](../virtual-switch).

### Switch and network adapter choices

Hyper-V offers three types of virtual switches and two types of virtual network adapters. You choose the type when you create the switch or adapter. You can use Hyper-V Manager or the Hyper-V module for Windows PowerShell to create and manage virtual switches and virtual network adapters. Some advanced networking capabilities, such as extended port access control lists (ACLs), can only be managed by using cmdlets in the Hyper-V module.

You can change an existing virtual switch to a different type after creation, but changing the virtual switch type affects the networking capabilities of all connected virtual machines. You can connect a virtual network adapter to a different virtual switch, but you can't change a virtual network adapter from one type to another; instead, add another virtual network adapter and choose the appropriate type.

Virtual switch types are:

- **External virtual switch** - Connects to a wired, physical network by binding to a physical network adapter.
- **Internal virtual switch** - Connects to a network that can be used only by the virtual machines running on the host that has the virtual switch, and between the host and the virtual machines.
- **Private virtual switch** - Connects to a network that can be used only by the virtual machines running on the host that has the virtual switch, but doesn't provide networking between the host and the virtual machines.

Virtual switch options:

| Setting name | Description |
| --- | --- |
| Allow management operating system to share this network adapter | Allow the Hyper-V host to share the use of the virtual switch and NIC or NIC team with the virtual machine. With this enabled, the host can use any of the settings that you configure for the virtual switch, such as Quality of Service (QoS) settings, security settings, or other features of the Hyper-V virtual switch. |
| Enable single-root I/O virtualization (SR-IOV) | Allow virtual machine traffic to bypass the virtual machine switch and go directly to the physical NIC. SR-IOV is only available for virtual machines running a [supported Windows Server guest](../supported-windows-guest-operating-systems-for-hyper-v-on-windows). For more information, see [Single-Root I/O Virtualization](/en-us/windows-hardware/drivers/network/overview-of-single-root-i-o-virtualization--sr-iov-). |

Virtual network adapter types:

| Adapter type | Key constraints and when to use |
| --- | --- |
| **Network adapter** (Hyper-V specific network adapter) | Available for generation 1 and generation 2 VMs. Requires a driver included in Hyper-V integration services, provided only for [supported guest operating systems](../supported-windows-guest-operating-systems-for-hyper-v-on-windows). Faster performance; recommended unless you need network boot or are running an unsupported guest OS. |
| **Legacy network adapter** | Generation 1 VMs only; not available for generation 2 VMs. Emulates an Intel 21140-based PCI Fast Ethernet Adapter. Use when you need to boot to a network to install an operating system (for example, via Windows Deployment Services). |

## Hyper-V networking and related technologies

Some features rely on specific networking configurations or perform better under certain configurations.

**Failover clustering** - It's a best practice to isolate cluster traffic and use Hyper-V Quality of Service (QoS) on the virtual switch.

**Live migration** - Use performance options to reduce network and CPU usage and the time it takes to complete a live migration. For instructions, see [Set up hosts for live migration without Failover Clustering](../deploy/set-up-hosts-for-live-migration-without-failover-clustering).

**Storage Spaces Direct** - Storage Spaces Direct relies on the SMB3.0 network protocol and RDMA. For details, see [Storage Spaces Direct overview](/en-us/azure/azure-local/concepts/storage-spaces-direct-overview?context=/windows-server/context/windows-server-storage).