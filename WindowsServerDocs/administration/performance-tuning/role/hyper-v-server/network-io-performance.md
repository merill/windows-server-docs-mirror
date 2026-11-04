---
layout: Conceptual
title: Hyper-V Network I/O Performance | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/role/hyper-v-server/network-io-performance
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Network i/o performance considerations in Hyper-V performance tuning
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: acb1db81-5cb2-c82c-035a-ec383969b8fa
document_version_independent_id: 2ab90bdb-79e2-c08a-de06-06aab31674bd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/role/hyper-v-server/network-io-performance.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/role/hyper-v-server/network-io-performance
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/role/hyper-v-server/network-io-performance.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: bb26cc32-184f-2b70-c455-ff33a2ca3418
---

# Hyper-V Network I/O Performance | Microsoft Learn

Server 2016 contains several improvements and new functionality to optimize network performance under Hyper-V. Documentation on how to optimize network performance will be included in a future version of this article.

## Live Migration

Live Migration lets you to transparently move running virtual machines from one node of a failover cluster to another node in the same cluster without a dropped network connection or perceived downtime.

Note

Failover Clustering requires shared storage for the cluster nodes.

The process of moving a running virtual machine can be divided into two major phases. The first phase copies the memory of the virtual machine from the current host to the new host. The second phase transfers the virtual machine state from the current host to the new host. The durations of both phases is greatly determined by the speed at which data can be transferred from the current host to the new host.

Providing a dedicated network for live migration traffic helps minimize the time that is required to complete a live migration, and it ensures consistent migration times.

![example hyper-v live migration configuration](../../media/perftune-guide-live-migration.png)

Additionally, increasing the number of send and receive buffers on each network adapter that is involved in the migration can improve migration performance.

Windows Server 2012 R2 introduced an option to speed up Live Migration by compressing memory before transferring over the network or use Remote Direct Memory Access (RDMA), if your hardware supports it.

## Additional References

- [Hyper-V terminology](terminology)
- [Hyper-V architecture](architecture)
- [Hyper-V server configuration](configuration)
- [Hyper-V processor performance](processor-performance)
- [Hyper-V memory performance](memory-performance)
- [Hyper-V storage I/O performance](storage-io-performance)
- [Detecting bottlenecks in a virtualized environment](detecting-virtualized-environment-bottlenecks)
- [Linux Virtual Machines](linux-virtual-machine-considerations)