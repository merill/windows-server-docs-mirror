---
layout: Conceptual
title: Network Subsystem Performance Tuning | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/network-subsystem/net-sub-performance-top
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn about the network subsystem and for links to other topics in this guide.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-27T00:00:00.0000000Z
locale: en-us
document_id: e6a14572-0559-d051-9881-733dea97d173
document_version_independent_id: 78782086-b2e1-99a9-0489-0418be2ee361
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/network-subsystem/net-sub-performance-top.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/network-subsystem/net-sub-performance-top
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/network-subsystem/net-sub-performance-top.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e25d1cf0-28d2-0083-0538-83ca58c0c98e
---

# Network Subsystem Performance Tuning | Microsoft Learn

You can use this topic for an overview of the network subsystem and for links to other topics in this guide.

Note

In addition to this topic, the following sections of this guide provide performance tuning recommendations for network devices and the network stack.

- [Choosing a Network Adapter](net-sub-choose-nic)
- [Configure the Order of Network Interfaces](net-sub-interface-metric)
- [Performance Tuning Network Adapters](net-sub-performance-tuning-nics)
- [Network-Related Performance Counters](net-sub-performance-counters)
- [Performance Tools for Network Workloads](net-sub-performance-tools)

Performance tuning the network subsystem, particularly for network intensive workloads, can involve each layer of the network architecture, which is also called the network stack. These layers are broadly divided into the following sections.

1. **Network interface**. This is the lowest layer in the network stack, and contains the network driver that communicates directly with the network adapter.
2. **Network Driver Interface Specification (NDIS)**. NDIS exposes interfaces for the driver below it and for the layers above it, such as the Protocol Stack.
3. **Protocol Stack**. The protocol stack implements protocols such as TCP/IP and UDP/IP. These layers expose the transport layer interface for layers above them.
4. **System Drivers**. These are typically clients that use a transport data extension (TDX) or Winsock Kernel (WSK) interface to expose interfaces to user-mode applications. The WSK interface was introduced in Windows Server 2008 and Windows® Vista, and it is exposed by AFD.sys. The interface improves performance by eliminating the switching between user mode and kernel mode.
5. **User-Mode Applications**. These are typically Microsoft solutions or custom applications.

The table below provides a vertical illustration of the layers of the network stack, including examples of items that run in each layer.

![Network Stack Layers](../../media/network-subsystem/network-layers.jpg)