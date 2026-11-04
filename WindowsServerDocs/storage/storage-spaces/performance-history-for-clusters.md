---
layout: Conceptual
title: Performance history for clusters | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/performance-history-for-clusters
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: 'Learn more about: Performance history for clusters'
ms.author: roharwoo
ms.topic: concept-article
author: robinharwood
ms.date: 2018-02-02T00:00:00.0000000Z
locale: en-us
document_id: b200e5f5-cead-e35d-12d0-958458404a12
document_version_independent_id: 95a5db21-bc26-eb9d-6e56-40a7ab24dad4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/performance-history-for-clusters.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/performance-history-for-clusters
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/performance-history-for-clusters.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 470e6c43-b882-79e9-2231-5a4888351803
---

# Performance history for clusters | Microsoft Learn

This sub-topic of [Performance history for Storage Spaces Direct](performance-history) describes the performance history collected for clusters.

There are no series that originate at the cluster level. Instead, server series, such as `clusternode.cpu.usage`, are aggregated for all servers in the cluster. Volume series, such as `volume.iops.total`, are aggregated for all volumes in the cluster. And drive series, such as `physicaldisk.size.total`, are aggregated for all drives in the cluster.

## Usage in PowerShell

Use the [Get-Cluster](/en-us/powershell/module/failoverclusters/get-cluster) cmdlet:

```PowerShell
Get-Cluster | Get-ClusterPerf
```

## Additional References

- [Performance history for Storage Spaces Direct](performance-history)