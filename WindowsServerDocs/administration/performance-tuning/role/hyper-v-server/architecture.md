---
layout: Conceptual
title: Hyper-V architecture | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/role/hyper-v-server/architecture
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Learn about the Hyper-V architecture considerations to tune and improve performance and lower costs.
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2025-01-10T00:00:00.0000000Z
locale: en-us
document_id: 9373c735-86ec-5738-ccfe-4b406140ac85
document_version_independent_id: 3b2d39bf-0c1a-6bf6-c23a-ae8a491ce8fc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/role/hyper-v-server/architecture.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/role/hyper-v-server/architecture
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/role/hyper-v-server/architecture.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: de216434-c23f-6170-4f2e-838e9d1f8d06
---

# Hyper-V architecture | Microsoft Learn

Hyper-V features a Type 1 hypervisor-based architecture. The hypervisor virtualizes processors and memory. It provides mechanisms for the virtualization stack in the root partition to manage child partitions, virtual machines (VMs) and expose services such as I/O (input/output) devices to the VMs.

The root partition owns and has direct access to the physical I/O devices. The virtualization stack in the root partition provides a memory manager for VMs, management APIs, and virtualized I/O devices. It also implements emulated devices, such as the integrated device electronics (IDE) disk controller and PS/2 input device port. And it supports Hyper-V-specific synthetic devices for increased performance and reduced overhead.

![Diagram showing the Hyper-V hypervisor-based architecture.](../../media/perftune-guide-hyperv-arch.png)

The Hyper-V-specific I/O architecture consists of virtualization service providers (VSPs) in the root partition and virtualization service clients (VSCs) in the child partition. Each service is exposed as a device over VM Bus, which acts as an I/O bus and enables high-performance communication between VMs that use mechanisms such as shared memory. The guest operating system's Plug and Play manager enumerates these devices, including VM Bus, and loads the appropriate device drivers, virtual service clients. Services other than I/O are also exposed through this architecture.

The following links suggest best practices that increase performance on servers running Hyper-V role.

- [Hyper-V terminology](terminology)
- [Hyper-V server configuration](configuration)
- [Hyper-V processor performance](processor-performance)
- [Hyper-V memory performance](memory-performance)
- [Hyper-V storage I/O performance](storage-io-performance)
- [Hyper-V network I/O performance](network-io-performance)
- [Detecting bottlenecks in a virtualized environment](detecting-virtualized-environment-bottlenecks)
- [Linux VMs](linux-virtual-machine-considerations)