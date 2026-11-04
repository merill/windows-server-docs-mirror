---
layout: Conceptual
title: Performance history for network adapters | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/performance-history-for-network-adapters
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: 'Learn more about: Performance history for network adapters'
ms.author: roharwoo
ms.topic: concept-article
author: robinharwood
ms.date: 2018-02-02T00:00:00.0000000Z
locale: en-us
document_id: edac17b7-8e38-8aff-886f-042b345f93cb
document_version_independent_id: f6994bd8-a75d-3fbc-c094-63e2bf86580f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/performance-history-for-network-adapters.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/performance-history-for-network-adapters
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/performance-history-for-network-adapters.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 6b9df392-e181-7e28-fd72-10a534462882
---

# Performance history for network adapters | Microsoft Learn

This sub-topic of [Performance history for Storage Spaces Direct](performance-history) describes in detail the performance history collected for network adapters. Network adapter performance history is available for every physical network adapter in every server in the cluster. Remote Direct Memory Access (RDMA) performance history is available for every physical network adapter with RDMA enabled.

Note

Performance history cannot be collected for network adapters in a server that is down. Collection will resume automatically when the server comes back up.

## Series names and units

These series are collected for every eligible network adapter:

| Series | Unit |
| --- | --- |
| `netadapter.bandwidth.inbound` | bits per second |
| `netadapter.bandwidth.outbound` | bits per second |
| `netadapter.bandwidth.total` | bits per second |
| `netadapter.bandwidth.rdma.inbound` | bits per second |
| `netadapter.bandwidth.rdma.outbound` | bits per second |
| `netadapter.bandwidth.rdma.total` | bits per second |

Note

Network adapter performance history is recorded in **bits per second**, not bytes per second. One 10 GbE (gigabit Ethernet) network adapter can send and receive approximately 10,000,000,000 bits per second = 1,250,000,000 bytes per second = 1.25 GB/s (gigabytes per second) at its theoretical maximum.

## How to interpret

| Series | How to interpret |
| --- | --- |
| `netadapter.bandwidth.inbound` | Rate of data received by the network adapter. |
| `netadapter.bandwidth.outbound` | Rate of data sent by the network adapter. |
| `netadapter.bandwidth.total` | Total rate of data received or sent by the network adapter. |
| `netadapter.bandwidth.rdma.inbound` | Rate of data received over RDMA by the network adapter. |
| `netadapter.bandwidth.rdma.outbound` | Rate of data sent over RDMA by the network adapter. |
| `netadapter.bandwidth.rdma.total` | Total rate of data received or sent over RDMA by the network adapter. |

## Where they come from

The `bytes.*` series are collected from the `Network Adapter` performance counter set on the server where the network adapter is installed, one instance per network adapter.

| Series | Source counter |
| --- | --- |
| `netadapter.bandwidth.inbound` | 8 × `Bytes Received/sec` |
| `netadapter.bandwidth.outbound` | 8 × `Bytes Sent/sec` |
| `netadapter.bandwidth.total` | 8 × `Bytes Total/sec` |

The `rdma.*` series are collected from the `RDMA Activity` performance counter set on the server where the network adapter is installed, one instance per network adapter with RDMA enabled.

| Series | Source counter |
| --- | --- |
| `netadapter.bandwidth.rdma.inbound` | 8 × `Inbound bytes/sec` |
| `netadapter.bandwidth.rdma.outbound` | 8 × `Outbound bytes/sec` |
| `netadapter.bandwidth.rdma.total` | 8 × *sum of the above* |

Note

Counters are measured over the entire interval, not sampled. For example, if the network adapter is idle for 9 seconds but transfers 200 bits in the 10th second, its `netadapter.bandwidth.total` will be recorded as 20 bits per second on average during this 10-second interval. This ensures its performance history captures all activity and is robust to noise.

## Usage in PowerShell

Use the [Get-NetAdapter](/en-us/powershell/module/netadapter/get-netadapter) cmdlet:

```PowerShell
Get-NetAdapter <Name> | Get-ClusterPerf
```

## Additional References

- [Performance history for Storage Spaces Direct](performance-history)