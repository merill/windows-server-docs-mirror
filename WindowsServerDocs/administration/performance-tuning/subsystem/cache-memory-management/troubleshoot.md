---
layout: Conceptual
title: Troubleshoot Cache and Memory Manager Performance Issues | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/subsystem/cache-memory-management/troubleshoot
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Troubleshoot Cache and Memory Manager Performance Issues on Windows Server 2016
ms.topic: troubleshooting-general
ms.author: roharwoo
author: robinharwood
ms.date: 2023-02-07T00:00:00.0000000Z
locale: en-us
document_id: 6fe81add-b285-ff8e-f383-2df80332e722
document_version_independent_id: 4e96ec10-8088-0d77-bc8b-d2197aebf9d9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/subsystem/cache-memory-management/troubleshoot.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/subsystem/cache-memory-management/troubleshoot
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/subsystem/cache-memory-management/troubleshoot.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f9cf537e-3e5a-4f31-a8e2-d06c28985eda
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b0200c40-0bea-4a73-a79b-8c68e19d3d16
platformId: bc480a59-e99a-8c8f-b022-df8959b2d3c5
---

# Troubleshoot Cache and Memory Manager Performance Issues | Microsoft Learn

Before Windows Server 2012, two primary potential issues caused system file cache to grow until available memory was almost depleted under certain workloads. When this situation results in the system being sluggish, you can determine whether the server is facing one of these issues.

## Counters to monitor

- Memory\Long-Term Average Standby Cache Lifetime (s) &lt; 1800 seconds
- Memory\Available (in Bytes, KBytes, or MBytes)
- Memory\System Cache Resident Bytes

If Memory\Available Mbytes is low and at the same time Memory\System Cache Resident Bytes is consuming significant part of the physical memory, you can use [RAMMAP](/en-us/sysinternals/downloads/rammap) to find out what the cache is being used for.

## System file cache contains NTFS metafile data structures

This problem is indicated by a high number of active Metafile pages in RAMMAP output, as shown in the following figure. This problem might have been observed on busy servers with millions of files being accessed, thereby resulting in caching NTFS metafile data not being released from the cache.

![rammap view](../../media/perftune-guide-rammap.png)

The problem used to be mitigated by *DynCache* tool. In Windows Server 2012+, the architecture has been redesigned and this problem should no longer exist.

## System file cache contains memory mapped files

This problem is indicated by a high number of active Mapped file pages in RAMMAP output. This usually indicates that some application on the server is opening numerous large files using [CreateFile](/en-us/windows/win32/api/fileapi/nf-fileapi-createfilea) API with `FILE_FLAG_RANDOM_ACCESS` flag set.

`FILE_FLAG_RANDOM_ACCESS` flag is a hint for Cache Manager to keep mapped views of the file in memory as long as possible (until Memory Manager doesn't signal low memory condition). At the same time, this flag instructs Cache Manager to disable prefetching of file data.

This situation has been mitigated to some extent by working set trimming improvements in Windows Server 2012+, but the issue itself needs to be primarily addressed by the application vendor by not using `FILE_FLAG_RANDOM_ACCESS`. An alternative solution for the app vendor might be to use low memory priority when accessing the files. This can be achieved using the [SetThreadInformation](/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadinformation) API. Pages that are accessed at low memory priority are removed from the working set more aggressively.

Cache Manager, starting in Windows Server 2016 further mitigates this by ignoring `FILE_FLAG_RANDOM_ACCESS` when making trimming decisions, so it's treated just like any other file opened without the `FILE_FLAG_RANDOM_ACCESS` flag (Cache Manager still honors this flag to disable prefetching of file data). You can still cause system cache bloat if you have large number of files opened with this flag and accessed in truly random fashion. It's highly recommended that `FILE_FLAG_RANDOM_ACCESS` not be used by applications.

## Remote file dirty page threshold is consistently exceeded

This problem is indicated if a system experiences occasional slowdowns during writes from a remote client. This issue might occur when a large amount of data is written from a fast remote client to a slow server destination.

Prior to Windows Server 2016, in such a scenario, if the dirty page threshold in the cache is reached, further writes will behave as if there were write-through. This can cause a flush of a large amount of data to the disk, which can lead to long delays if the storage is slow, resulting in timeouts for the remote connection.

In Window Server 2016 and forward, a mitigation is put in place to reduce the likelihood of timeouts. A separate dirty page threshold for remote writes is implemented, and an inline flush will be performed when it's exceeded. This can result on occasional slowdowns during heavy write activity, but eliminates the risk of a timeout in most cases. This remote dirty page threshold is **5 GB per file** by default. For some configurations and workloads, a different number performs better.

If the default size of 5 GB doesn't work well for your configuration, it's recommended to try increasing the limit in 256-MB increments until performance is satisfactory. Be aware of the following:

- A reboot is required for changes to this registry key to take effect.
- The units of RemoteFileDirtyPageThreshold are **number of pages** (with page size as managed by Cache Manager). This means it should be set to the desired size in bytes, divided by 4096.
- Recommended values are 128 MB &lt;= N &lt;= 50% of available memory.
- This threshold can be disabled completely by setting it to -1. **This is not recommended** as it can result in timeouts for remote connections.

For example, if you want to set the limit to 10GiB that's 10,737,418,240 bytes / 4096 = 2,621,440 which is a decimal DWORD value of 2621440.

This threshold can be controlled using the following registry value.

- **Key**: `HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management`
    - **Type**: `DWORD`
    - **Value name**: `RemoteFileDirtyPageThreshold`
    - **Value data**: Decimal - Number of pages (page size as managed by Cache Manager).