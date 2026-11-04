---
layout: Conceptual
title: Performance Tuning for Cache and Memory Manager Subsystems | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/subsystem/cache-memory-management/
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Performance Tuning for Cache and Memory Manager Subsystems
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4c61832d-d71f-b462-79b4-f565e1623a6c
document_version_independent_id: 30567f86-3012-e5ac-1ad7-36341ca9daa1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/subsystem/cache-memory-management/index.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/subsystem/cache-memory-management/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/subsystem/cache-memory-management/index.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: f72d4937-2cba-f4f9-f161-f16619f54e1e
---

# Performance Tuning for Cache and Memory Manager Subsystems | Microsoft Learn

By default, Windows caches file data that is read from disks and written to disks. This implies that read operations read file data from an area in system memory, known as the system file cache, rather than from the physical disk. Correspondingly, write operations write file data to the system file cache rather than to the disk, and this type of cache is referred to as a write-back cache. Caching is managed per file object. Caching occurs under the direction of the Cache Manager, which operates continuously while Windows is running.

File data in the system file cache is written to the disk at intervals determined by the operating system. Flushed pages stay either in system cache working set (when FILE\_FLAG\_RANDOM\_ACCESS is set and file handle wasn't closed) or on the standby list where these become part of available memory.

The policy of delaying the writing of the data to the file and holding it in the cache until the cache is flushed is called lazy writing, and it is triggered by the Cache Manager at a determinate time interval. The time at which a block of file data is flushed is partially based on the amount of time it has been stored in the cache and the amount of time since the data was last accessed in a read operation. This ensures that file data that is frequently read will stay accessible in the system file cache for the maximum amount of time.

This file data caching process is illustrated in the following figure:

![file data caching](../../media/perftune-guide-file-data-caching.png)

As depicted by the solid arrows in the preceding figure, a 256 KB region of data is read into a 256 KB cache slot in system address space when it is first requested by the Cache Manager during a file read operation. A user-mode process then copies the data in this slot to its own address space. When the process has completed its data access, it writes the altered data back to the same slot in the system cache, as shown by the dotted arrow between the process address space and the system cache. When the Cache Manager has determined that the data will no longer be needed for a certain amount of time, it writes the altered data back to the file on the disk, as shown by the dotted arrow between the system cache and the disk.

**In this section:**

- [Cache and Memory Manager Potential Performance Issues](troubleshoot)
- [Cache and Memory Manager Improvements in Windows Server 2016](improvements-in-windows-server)