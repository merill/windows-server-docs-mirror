---
layout: Conceptual
title: Performance history for virtual hard disks | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/performance-history-for-vhds
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: 'Learn more about: Performance history for virtual hard disks'
ms.author: roharwoo
ms.topic: concept-article
author: robinharwood
ms.date: 2018-02-09T00:00:00.0000000Z
locale: en-us
document_id: 5f68ce14-d411-35e7-dbf3-af6451ff3056
document_version_independent_id: 71d9382d-4fc3-4091-eedb-38346ae9ec2c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/performance-history-for-vhds.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/performance-history-for-vhds
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/performance-history-for-vhds.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: fee0e4ae-54ec-802f-e2af-303be3766fc0
---

# Performance history for virtual hard disks | Microsoft Learn

This sub-topic of [Performance history for Storage Spaces Direct](performance-history) describes in detail the performance history collected for virtual hard disk (VHD) files. Performance history is available for every VHD attached to a running, clustered virtual machine. Performance history is available for both VHD and VHDX formats, however it is not available for Shared VHDX files.

Note

It may take several minutes for collection to begin for newly created or moved VHD files.

## Series names and units

These series are collected for every eligible virtual hard disk:

| Series | Unit |
| --- | --- |
| `vhd.iops.read` | per second |
| `vhd.iops.write` | per second |
| `vhd.iops.total` | per second |
| `vhd.throughput.read` | bytes per second |
| `vhd.throughput.write` | bytes per second |
| `vhd.throughput.total` | bytes per second |
| `vhd.latency.average` | seconds |
| `vhd.size.current` | bytes |
| `vhd.size.maximum` | bytes |

## How to interpret

| Series | How to interpret |
| --- | --- |
| `vhd.iops.read` | Number of read operations per second completed by the virtual hard disk. |
| `vhd.iops.write` | Number of write operations per second completed by the virtual hard disk. |
| `vhd.iops.total` | Total number of read or write operations per second completed by the virtual hard disk. |
| `vhd.throughput.read` | Quantity of data read from the virtual hard disk per second. |
| `vhd.throughput.write` | Quantity of data written to the virtual hard disk per second. |
| `vhd.throughput.total` | Total quantity of data read from or written to the virtual hard disk per second. |
| `vhd.latency.average` | Average latency of all operations to or from the virtual hard disk. |
| `vhd.size.current` | The current file size of the virtual hard disk, if dynamically expanding. If fixed, the series is not collected. |
| `vhd.size.maximum` | The maximum size of the virtual hard disk, if dynamically expanding. If fixed, the is the size. |

## Where they come from

The `iops.*`, `throughput.*`, and `latency.*` series are collected from the `Hyper-V Virtual Storage Device` performance counter set on the server where the virtual machine is running, one instance per VHD or VHDX.

| Series | Source counter |
| --- | --- |
| `vhd.iops.read` | `Read Operations/Sec` |
| `vhd.iops.write` | `Write Operations/Sec` |
| `vhd.iops.total` | *sum of the above* |
| `vhd.throughput.read` | `Read Bytes/sec` |
| `vhd.throughput.write` | `Write Bytes/sec` |
| `vhd.throughput.total` | *sum of the above* |
| `vhd.latency.average` | `Latency` |

Note

Counters are measured over the entire interval, not sampled. For example, if the VHD is inactive for 9 seconds but completes 30 IOs in the 10th second, its `vhd.iops.total` will be recorded as 3 IOs per second on average during this 10-second interval. This ensures its performance history captures all activity and is robust to noise.

## Usage in PowerShell

Use the [Get-VHD](/en-us/powershell/module/hyper-v/get-vhd) cmdlet:

```PowerShell
Get-VHD <Path> | Get-ClusterPerf
```

To get the path of every VHD from the virtual machine:

```PowerShell
(Get-VM <Name>).HardDrives | Select Path
```

Note

The Get-VHD cmdlet requires a file path to be provided. It does not support enumeration.

## Additional References

- [Performance history for Storage Spaces Direct](performance-history)