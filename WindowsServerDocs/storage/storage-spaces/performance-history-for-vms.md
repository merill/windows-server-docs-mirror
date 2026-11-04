---
layout: Conceptual
title: Performance history for virtual machines | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/performance-history-for-vms
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: 'Learn more about: Performance history for virtual machines'
ms.author: roharwoo
ms.topic: concept-article
author: robinharwood
ms.date: 2018-09-07T00:00:00.0000000Z
locale: en-us
document_id: a116df5a-5fea-c7b5-71af-bdd86ed710a0
document_version_independent_id: 04f1caa6-d2d7-e06c-7bb2-05e687b306a3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/performance-history-for-vms.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/performance-history-for-vms
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/performance-history-for-vms.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: a9bc82e6-5447-d427-2c1a-fc560bab5066
---

# Performance history for virtual machines | Microsoft Learn

This sub-topic of [Performance history for Storage Spaces Direct](performance-history) describes in detail the performance history collected for virtual machines (VM). Performance history is available for every running, clustered VM.

Note

It may take several minutes for collection to begin for newly created or renamed VMs.

## Series names and units

These series are collected for every eligible VM:

| Series | Unit |
| --- | --- |
| `vm.cpu.usage` | percent |
| `vm.memory.assigned` | bytes |
| `vm.memory.available` | bytes |
| `vm.memory.maximum` | bytes |
| `vm.memory.minimum` | bytes |
| `vm.memory.pressure` | - |
| `vm.memory.startup` | bytes |
| `vm.memory.total` | bytes |
| `vmnetworkadapter.bandwidth.inbound` | bits per second |
| `vmnetworkadapter.bandwidth.outbound` | bits per second |
| `vmnetworkadapter.bandwidth.total` | bits per second |

In addition, all virtual hard disk (VHD) series, such as `vhd.iops.total`, are aggregated for every VHD attached to the VM.

## How to interpret

| Series | Description |
| --- | --- |
| `vm.cpu.usage` | Percentage the virtual machine is using of its host server's processor(s). |
| `vm.memory.assigned` | The quantity of memory assigned to the virtual machine. |
| `vm.memory.available` | The quantity of memory that remains available, of the amount assigned. |
| `vm.memory.maximum` | If using dynamic memory, this is the maximum quantity of memory that may be assigned to the virtual machine. |
| `vm.memory.minimum` | If using dynamic memory, this is the minimum quantity of memory that may be assigned to the virtual machine. |
| `vm.memory.pressure` | The ratio of memory demanded by the virtual machine over memory allocated to the virtual machine. |
| `vm.memory.startup` | The quantity of memory required for the virtual machine to start. |
| `vm.memory.total` | Total memory. |
| `vmnetworkadapter.bandwidth.inbound` | Rate of data received by the virtual machine across all its virtual network adapters. |
| `vmnetworkadapter.bandwidth.outbound` | Rate of data sent by the virtual machine across all its virtual network adapters. |
| `vmnetworkadapter.bandwidth.total` | Total rate of data received or sent by the virtual machine across all its virtual network adapters. |

Note

Counters are measured over the entire interval, not sampled. For example, if the VM is idle for 9 seconds but spikes to use 50% of host CPU in the 10th second, its `vm.cpu.usage` will be recorded as 5% on average during this 10-second interval. This ensures its performance history captures all activity and is robust to noise.

## Usage in PowerShell

Use the [Get-VM](/en-us/powershell/module/hyper-v/get-vm) cmdlet:

```PowerShell
Get-VM <Name> | Get-ClusterPerf
```

Note

The Get-VM cmdlet only returns virtual machines on the local (or specified) server, not across the cluster.

## Additional References

- [Performance history for Storage Spaces Direct](performance-history)