---
layout: Conceptual
title: Performance Tuning Hyper-V Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/role/hyper-v-server/
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Performance tuning guidelines for Hyper-V
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2024-03-08T00:00:00.0000000Z
locale: en-us
document_id: a028c9f4-3c32-9459-2f5a-fdd535b28e5d
document_version_independent_id: 249e452f-a38c-a604-cc7d-1ae17a31d291
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/role/hyper-v-server/index.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/role/hyper-v-server/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/role/hyper-v-server/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/289b8734-3abd-4162-bc19-e661c3f4c940
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a94795e-9024-410d-b38e-b67941440893
platformId: 7b2245b7-7376-23d9-3621-554efda64c9d
---

# Performance Tuning Hyper-V Servers | Microsoft Learn

Hyper-V is the virtualization server role in Windows Server and Azure Local. Virtualization servers can host multiple virtual machines that are isolated from each other but share the underlying hardware resources by virtualizing the processors, memory, and I/O devices. By consolidating servers onto a single machine, virtualization can improve resource usage and energy efficiency and reduce the operational and maintenance costs of servers. In addition, virtual machines and the management APIs offer more flexibility for managing resources, balancing load, and provisioning systems.

## Additional References

- [Hyper-V terminology](terminology)
- [Hyper-V architecture](architecture)
- [Hyper-V server configuration](configuration)
- [Hyper-V processor performance](processor-performance)
- [Hyper-V memory performance](memory-performance)
- [Hyper-V storage I/O performance](storage-io-performance)
- [Hyper-V network I/O performance](network-io-performance)
- [Detecting bottlenecks in a virtualized environment](detecting-virtualized-environment-bottlenecks)
- [Linux Virtual Machines](linux-virtual-machine-considerations)