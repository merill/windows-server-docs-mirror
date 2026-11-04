---
layout: Conceptual
title: Performance history for volumes | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/performance-history-for-volumes
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: 'Learn more about: Performance history for volumes'
ms.author: roharwoo
ms.topic: concept-article
author: robinharwood
ms.date: 2018-02-09T00:00:00.0000000Z
locale: en-us
document_id: dafa247b-03b5-f5ba-89ba-08f80c1cf4be
document_version_independent_id: bda888e8-d9ab-970c-616b-ef0b2e0b4bb5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/performance-history-for-volumes.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/performance-history-for-volumes
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/performance-history-for-volumes.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 76fa61ab-b8e8-09c0-bb10-54bb173275c3
---

# Performance history for volumes | Microsoft Learn

This sub-topic of [Performance history for Storage Spaces Direct](performance-history) describes in detail the performance history collected for volumes. Performance history is available for every Cluster Shared Volume (CSV) in the cluster. However, it is not available for OS boot volumes nor any other non-CSV storage.

Note

It may take several minutes for collection to begin for newly created or renamed volumes.

## Series names and units

These series are collected for every eligible volume:

| Series | Unit |
| --- | --- |
| `volume.iops.read` | per second |
| `volume.iops.write` | per second |
| `volume.iops.total` | per second |
| `volume.throughput.read` | bytes per second |
| `volume.throughput.write` | bytes per second |
| `volume.throughput.total` | bytes per second |
| `volume.latency.read` | seconds |
| `volume.latency.write` | seconds |
| `volume.latency.average` | seconds |
| `volume.size.total` | bytes |
| `volume.size.available` | bytes |

## How to interpret

| Series | How to interpret |
| --- | --- |
| `volume.iops.read` | Number of read operations per second completed by this volume. |
| `volume.iops.write` | Number of write operations per second completed by this volume. |
| `volume.iops.total` | Total number of read or write operations per second completed by this volume. |
| `volume.throughput.read` | Quantity of data read from this volume per second. |
| `volume.throughput.write` | Quantity of data written to this volume per second. |
| `volume.throughput.total` | Total quantity of data read from or written to this volume per second. |
| `volume.latency.read` | Average latency of read operations from this volume. |
| `volume.latency.write` | Average latency of write operations to this volume. |
| `volume.latency.average` | Average latency of all operations to or from this volume. |
| `volume.size.total` | The total storage capacity of the volume. |
| `volume.size.available` | The available storage capacity of the volume. |

## Where they come from

The `iops.*`, `throughput.*`, and `latency.*` series are collected from the `Cluster CSVFS` performance counter set. Every server in the cluster has an instance for every CSV volume, regardless of ownership. The performance history recorded for volume `MyVolume` is the aggregate of the `MyVolume` instances on every server in the cluster.

| Series | Source counter |
| --- | --- |
| `volume.iops.read` | `Reads/sec` |
| `volume.iops.write` | `Writes/sec` |
| `volume.iops.total` | *sum of the above* |
| `volume.throughput.read` | `Read bytes/sec` |
| `volume.throughput.write` | `Write bytes/sec` |
| `volume.throughput.total` | *sum of the above* |
| `volume.latency.read` | `Avg. sec/Read` |
| `volume.latency.write` | `Avg. sec/Write` |
| `volume.latency.average` | *average of the above* |

Note

Counters are measured over the entire interval, not sampled. For example, if the volume is idle for 9 seconds but completes 30 IOs in the 10th second, its `volume.iops.total` will be recorded as 3 IOs per second on average during this 10-second interval. This ensures its performance history captures all activity and is robust to noise.

Tip

These are the same counters used by the popular [VM Fleet](https://github.com/microsoft/diskspd/blob/master/Frameworks/VMFleet/WatchCluster.psm1) benchmark framework.

The `size.*` series are collected from the `MSFT_Volume` class in WMI, one instance per volume.

| Series | Source property |
| --- | --- |
| `volume.size.total` | `Size` |
| `volume.size.available` | `SizeRemaining` |

## Usage in PowerShell

Use the [Get-Volume](/en-us/powershell/module/storage/get-volume) cmdlet:

```PowerShell
Get-Volume -FriendlyName <FriendlyName> | Get-ClusterPerf
```

## Additional References

- [Performance history for Storage Spaces Direct](performance-history)