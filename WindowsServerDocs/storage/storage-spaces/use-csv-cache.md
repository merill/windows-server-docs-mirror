---
layout: Conceptual
title: Use the CSV in-memory read cache with Azure Local and Windows Server clusters | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-spaces/use-csv-cache
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage-spaces
ms.update-cycle: 1095-days
description: This topic describes how to use system memory to boost performance.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.reviewer: jgerend
ms.date: 2023-04-19T00:00:00.0000000Z
locale: en-us
document_id: 996a34f4-0320-ecb4-ee8d-014bd13d788f
document_version_independent_id: 996a34f4-0320-ecb4-ee8d-014bd13d788f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-spaces/use-csv-cache.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-spaces/use-csv-cache
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-spaces/use-csv-cache.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/289b8734-3abd-4162-bc19-e661c3f4c940
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a94795e-9024-410d-b38e-b67941440893
platformId: 8f659153-bfee-b355-8b5f-107c5ca78865
---

# Use the CSV in-memory read cache with Azure Local and Windows Server clusters | Microsoft Learn

This topic describes how to use system memory to boost the performance of Azure Local and Windows Server by caching frequent reads. Writes cannot be cached in memory.

Azure Local and Windows Server are compatible with the Cluster Shared Volume (CSV) in-memory read cache. Using system memory to cache reads can improve performance for applications like Hyper-V, which uses unbuffered I/O to access VHD or VHDX files. (Unbuffered I/Os are any operations that are not cached by the Windows Cache Manager.)

Because the in-memory cache is server-local, it improves data locality. Recent reads are cached in memory on the same host where the virtual machine (VM) is running, reducing how often reads go over the network. This results in lower latency and better storage performance.

Note that the CSV in-memory read cache is different from the [storage pool cache](cache).

## Planning considerations

The in-memory read cache is most effective for read-intensive workloads, such as Virtual Desktop Infrastructure (VDI). Conversely, if the workload is extremely write-intensive, the cache may introduce more overhead than value and should be disabled.

You can use up to 80% of total physical memory for the CSV in-memory read cache. Be careful to leave enough memory for your VMs!

Note

Certain microbenchmarking tools like DISKSPD and [VM Fleet](https://github.com/Microsoft/diskspd/tree/master/Frameworks/VMFleet) may produce worse results with the CSV in-memory read cache enabled than without it. By default VM Fleet creates one 10 GiB VHDX per VM – approximately 1 TiB total for 100 VMs – and then performs *uniformly random* reads and writes to them. Unlike real workloads, the reads don't follow any predictable or repetitive pattern, so the in-memory cache is not effective and just incurs overhead.

## Configuring the in-memory read cache

The CSV in-memory read cache is available in Azure Local, Windows Server 2019, and Windows Server 2016 with the same functionality. In Azure Local and Windows Server 2019, it's on by default with 1 gibibyte (GiB) allocated. In Windows Server 2016, it's off by default.

| OS version | Default CSV cache size |
| --- | --- |
| Azure Local | 1 GiB |
| Windows Server 2019 | 1 GiB |
| Windows Server 2016 | 0 (disabled) |

### Configure the cache using Windows Admin Center

To configure the cache using Windows Admin Center, do the following:

1. In Windows Admin Center, connect to a cluster, and then select **Settings** from the **Tools** pane on the left.
2. Select **In-memory cache** under **Storage** on the **Settings** pane.
3. In the right pane, a checkbox enables or disables the cache, and you can also specify the maximum memory per server to be allocated to the cache.
4. When done, select **Save**.

[![In Windows Admin Center, a checkbox enables or disables the cache. You can also specify the maximum memory per server to be allocated to the cache.](media/use-csv-cache/in-memory-cache.png)](media/use-csv-cache/in-memory-cache.png#lightbox)

### Configure the cache using PowerShell

To see how much memory is allocated using PowerShell, run the following as administrator:

```PowerShell
(Get-Cluster).BlockCacheSize
```

The value returned is in mebibytes (MiB) per server. For example, `1024` represents 1 GiB.

To change how much memory is allocated, modify this value using PowerShell. For example, to allocate 2 GiB per server, run:

```PowerShell
(Get-Cluster).BlockCacheSize = 2048
```

For changes to take effect immediately, pause and then resume your CSV volumes, or move them between servers. For example, use this PowerShell fragment to move each CSV to another server node and back again:

```PowerShell
Get-ClusterSharedVolume | ForEach {
    $Owner = $_.OwnerNode
    $_ | Move-ClusterSharedVolume
    $_ | Move-ClusterSharedVolume -Node $Owner
}
```