---
layout: Conceptual
title: Performance history for drives | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/performance-history-for-drives
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: 'Learn more about: Performance history for drives'
ms.author: roharwoo
ms.topic: concept-article
author: robinharwood
ms.date: 2018-02-02T00:00:00.0000000Z
locale: en-us
document_id: 99b7d4ea-d38d-d8e4-3056-f4aba683f80d
document_version_independent_id: 3e5cb3ec-2669-a84e-4404-62493ed6ba2f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/performance-history-for-drives.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/performance-history-for-drives
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/performance-history-for-drives.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: a9909812-777b-0349-c46c-afc137a86552
---

# Performance history for drives | Microsoft Learn

This sub-topic of [Performance history for Storage Spaces Direct](performance-history) describes in detail the performance history collected for drives. Performance history is available for every drive in the cluster storage subsystem, regardless of bus or media type. However, it is not available for OS boot drives.

Note

Performance history cannot be collected for drives in a server that is down. Collection will resume automatically when the server comes back up.

## Series names and units

These series are collected for every eligible drive:

| Series | Unit |
| --- | --- |
| `physicaldisk.iops.read` | per second |
| `physicaldisk.iops.write` | per second |
| `physicaldisk.iops.total` | per second |
| `physicaldisk.throughput.read` | bytes per second |
| `physicaldisk.throughput.write` | bytes per second |
| `physicaldisk.throughput.total` | bytes per second |
| `physicaldisk.latency.read` | seconds |
| `physicaldisk.latency.write` | seconds |
| `physicaldisk.latency.average` | seconds |
| `physicaldisk.size.total` | bytes |
| `physicaldisk.size.used` | bytes |

## How to interpret

| Series | How to interpret |
| --- | --- |
| `physicaldisk.iops.read` | Number of read operations per second completed by the drive. |
| `physicaldisk.iops.write` | Number of write operations per second completed by the drive. |
| `physicaldisk.iops.total` | Total number of read or write operations per second completed by the drive. |
| `physicaldisk.throughput.read` | Quantity of data read from the drive per second. |
| `physicaldisk.throughput.write` | Quantity of data written to the drive per second. |
| `physicaldisk.throughput.total` | Total quantity of data read from or written to the drive per second. |
| `physicaldisk.latency.read` | Average latency of read operations from the drive. |
| `physicaldisk.latency.write` | Average latency of write operations to the drive. |
| `physicaldisk.latency.average` | Average latency of all operations to or from the drive. |
| `physicaldisk.size.total` | The total storage capacity of the drive. |
| `physicaldisk.size.used` | The used storage capacity of the drive. |

## Where they come from

The `iops.*`, `throughput.*`, and `latency.*` series are collected from the `Physical Disk` performance counter set on the server where the drive is connected, one instance per drive. These counters are measured by `partmgr.sys` and do not include much of the Windows software stack nor any network hops. They are representative of device hardware performance.

| Series | Source counter |
| --- | --- |
| `physicaldisk.iops.read` | `Disk Reads/sec` |
| `physicaldisk.iops.write` | `Disk Writes/sec` |
| `physicaldisk.iops.total` | `Disk Transfers/sec` |
| `physicaldisk.throughput.read` | `Disk Read Bytes/sec` |
| `physicaldisk.throughput.write` | `Disk Write Bytes/sec` |
| `physicaldisk.throughput.total` | `Disk Bytes/sec` |
| `physicaldisk.latency.read` | `Avg. Disk sec/Read` |
| `physicaldisk.latency.write` | `Avg. Disk sec/Writes` |
| `physicaldisk.latency.average` | `Avg. Disk sec/Transfer` |

Note

Counters are measured over the entire interval, not sampled. For example, if the drive is idle for 9 seconds but completes 30 IOs in the 10th second, its `physicaldisk.iops.total` will be recorded as 3 IOs per second on average during this 10-second interval. This ensures its performance history captures all activity and is robust to noise.

The `size.*` series are collected from the `MSFT_PhysicalDisk` class in WMI, one instance per drive.

| Series | Source property |
| --- | --- |
| `physicaldisk.size.total` | `Size` |
| `physicaldisk.size.used` | `VirtualDiskFootprint` |

## Usage in PowerShell

Use the [Get-PhysicalDisk](/en-us/powershell/module/storage/get-physicaldisk) cmdlet:

```PowerShell
Get-PhysicalDisk -SerialNumber <SerialNumber> | Get-ClusterPerf
```

## Additional References

- [Performance history for Storage Spaces Direct](performance-history)