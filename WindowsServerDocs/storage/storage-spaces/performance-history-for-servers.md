---
layout: Conceptual
title: Performance history for servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/performance-history-for-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: 'Learn more about: Performance history for servers'
ms.author: roharwoo
ms.topic: concept-article
author: robinharwood
ms.date: 2018-02-05T00:00:00.0000000Z
locale: en-us
document_id: 83220e3d-12ff-aea2-d4f4-1301f83f49af
document_version_independent_id: 2b6151a1-37dd-d2b7-f14b-1ff6a033839b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/performance-history-for-servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/performance-history-for-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/performance-history-for-servers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c09a8f62-9778-097e-00f6-a6b8fa805daa
---

# Performance history for servers | Microsoft Learn

This sub-topic of [Performance history for Storage Spaces Direct](performance-history) describes in detail the performance history collected for servers. Performance history is available for every server in the cluster.

Note

Performance history cannot be collected for a server that is down. Collection will resume automatically when the server comes back up.

## Series names and units

These series are collected for every eligible server:

| Series | Unit |
| --- | --- |
| `clusternode.cpu.usage` | percent |
| `clusternode.cpu.usage.guest` | percent |
| `clusternode.cpu.usage.host` | percent |
| `clusternode.memory.total` | bytes |
| `clusternode.memory.available` | bytes |
| `clusternode.memory.usage` | bytes |
| `clusternode.memory.usage.guest` | bytes |
| `clusternode.memory.usage.host` | bytes |

In addition, drive series such as `physicaldisk.size.total` are aggregated for all eligible drives attached to the server, and network adapter series such as `networkadapter.bytes.total` are aggregated for all eligible network adapters attached to the server.

## How to interpret

| Series | How to interpret |
| --- | --- |
| `clusternode.cpu.usage` | Percentage of processor time that is not idle. |
| `clusternode.cpu.usage.guest` | Percentage of processor time used for guest (virtual machine) demand. |
| `clusternode.cpu.usage.host` | Percentage of processor time used for host demand. |
| `clusternode.memory.total` | The total physical memory of the server. |
| `clusternode.memory.available` | The available memory of the server. |
| `clusternode.memory.usage` | The allocated (not available) memory of the server. |
| `clusternode.memory.usage.guest` | The memory allocated to guest (virtual machine) demand. |
| `clusternode.memory.usage.host` | The memory allocated to host demand. |

## Where they come from

The `cpu.*` series are collected from different performance counters depending on whether or not Hyper-V is enabled.

If Hyper-V is enabled:

| Series | Source counter |
| --- | --- |
| `clusternode.cpu.usage` | `Hyper-V Hypervisor Logical Processor` &gt; `_Total` &gt; `% Total Run Time` |
| `clusternode.cpu.usage.guest` | `Hyper-V Hypervisor Virtual Processor` &gt; `_Total` &gt; `% Total Run Time` |
| `clusternode.cpu.usage.host` | `Hyper-V Hypervisor Root Virtual Processor` &gt; `_Total` &gt; `% Total Run Time` |

Using the `% Total Run Time` counters ensures that performance history attributes all usage.

If Hyper-V is NOT enabled:

| Series | Source counter |
| --- | --- |
| `clusternode.cpu.usage` | `Processor` &gt; `_Total` &gt; `% Processor Time` |
| `clusternode.cpu.usage.guest` | *zero* |
| `clusternode.cpu.usage.host` | *same as total usage* |

Notwithstanding imperfect synchronization, `clusternode.cpu.usage` is always `clusternode.cpu.usage.host` plus `clusternode.cpu.usage.guest`.

With the same caveat, `clusternode.cpu.usage.guest` is always the sum of `vm.cpu.usage` for all virtual machines on the host server.

The `memory.*` series are (COMING SOON).

Note

Counters are measured over the entire interval, not sampled. For example, if the server is idle for 9 seconds but spikes to 100% CPU in the 10th second, its `clusternode.cpu.usage` will be recorded as 10% on average during this 10-second interval. This ensures its performance history captures all activity and is robust to noise.

## Usage in PowerShell

Use the [Get-ClusterNode](/en-us/powershell/module/failoverclusters/get-clusternode) cmdlet:

```PowerShell
Get-ClusterNode <Name> | Get-ClusterPerf
```

## Additional References

- [Performance history for Storage Spaces Direct](performance-history)