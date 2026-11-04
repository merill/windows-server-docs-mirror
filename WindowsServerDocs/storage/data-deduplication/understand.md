---
layout: Conceptual
title: Understanding Data Deduplication | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/data-deduplication/understand
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: 'Learn more about: Understanding Data Deduplication'
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2022-02-18T00:00:00.0000000Z
locale: en-us
document_id: 18e6e255-efad-fb38-ec56-d78918c0e744
document_version_independent_id: 1b0231ac-fbf1-d3ed-c12a-5c8b2aaa4d4a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/data-deduplication/understand.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/data-deduplication/understand
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/data-deduplication/understand.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d774b87-7dcb-40bf-a0b9-5a7a9efff0d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/89dc5f37-0e4e-4b05-ad87-5fcd2b941a8a
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 65c644d3-9063-2a50-d90e-2e6c860cdfa6
---

# Understanding Data Deduplication | Microsoft Learn

This document describes how [Data Deduplication](overview) works.

## How does Data Deduplication work?

Data Deduplication in Windows Server was created with the following two principles:

1. **Optimization should not get in the way of writes to the disk** Data Deduplication optimizes data by using a post-processing model. All data is written unoptimized to the disk and then optimized later by Data Deduplication.
2. **Optimization should not change access semantics** Users and applications that access data on an optimized volume are completely unaware that the files they are accessing have been deduplicated.

Once enabled for a volume, Data Deduplication runs in the background to:

- Identify repeated patterns across files on that volume.
- Seamlessly move those portions, or chunks, with special pointers called reparse points that point to a unique copy of that chunk.

This occurs in the following four steps:

1. Scan the file system for files meeting the optimization policy.![Scan file system](media/understanding-dedup-how-dedup-works-1.gif)
2. Break files into variable-size chunks.![Break files into chunks](media/understanding-dedup-how-dedup-works-2.gif)
3. Identify unique chunks.![Identify unique chunks](media/understanding-dedup-how-dedup-works-3.gif)
4. Place chunks in the chunk store and optionally compress.![Move to Chunk Store](media/understanding-dedup-how-dedup-works-4.gif)
5. Replace the original file stream of now optimized files with a reparse point to the chunk store.![Replace file stream with reparse point](media/understanding-dedup-how-dedup-works-5.gif)

When optimized files are read, the file system sends the files with a reparse point to the Data Deduplication file system filter (Dedup.sys). The filter redirects the read operation to the appropriate chunks that constitute the stream for that file in the chunk store. Modifications to ranges of a deduplicated files get written unoptimized to the disk and are optimized by the [Optimization job](understand#job-info) the next time it runs.

## Usage Types

The following Usage Types provide reasonable Data Deduplication configuration for common workloads:

| Usage Type | Ideal workloads | What's different |
| --- | --- | --- |
| Default | General purpose file server:<br>- Team shares<br>- Work Folders<br>- Folder redirection<br>- Software development shares | - Background optimization<br>- Default optimization policy:<br>    - Minimum file age = 3 days<br>    - Optimize in-use files = No<br>    - Optimize partial files = No |
| Hyper-V | Virtualized Desktop Infrastructure (VDI) servers | - Background optimization<br>- Default optimization policy:<br>    - Minimum file age = 3 days<br>    - Optimize in-use files = Yes<br>    - Optimize partial files = Yes<br>- "Under-the-hood" tweaks for Hyper-V interop |
| Backup | Virtualized backup applications, such as [Microsoft Data Protection Manager (DPM)](/en-us/previous-versions/system-center/system-center-2012-R2/hh758173%28v=sc.12%29) | - Priority optimization<br>- Default optimization policy:<br>    - Minimum file age = 0 days<br>    - Optimize in-use files = Yes<br>    - Optimize partial files = No<br>- "Under-the-hood" tweaks for interop with DPM/DPM-like solutions |

## Jobs

Data Deduplication uses a post-processing strategy to optimize and maintain a volume's space efficiency.

| Job name | Job descriptions | Default schedule |
| --- | --- | --- |
| Optimization | The **Optimization** job deduplicates by chunking data on a volume per the volume policy settings, (optionally) compressing those chunks, and storing chunks uniquely in the chunk store. The optimization process that Data Deduplication uses is described in detail in [How does Data Deduplication work?](understand#how-does-dedup-work). | Once every hour |
| Garbage Collection | The **Garbage Collection** job reclaims disk space by removing unnecessary chunks that are no longer being referenced by files that have been recently modified or deleted. | Every Saturday at 2:35 AM |
| Integrity Scrubbing | The **Integrity Scrubbing** job identifies corruption in the chunk store due to disk failures or bad sectors. When possible, Data Deduplication can automatically use volume features (such as mirror or parity on a Storage Spaces volume) to reconstruct the corrupted data. Additionally, Data Deduplication keeps backup copies of popular chunks when they are referenced more than 100 times in an area called the hotspot. | Every Saturday at 3:35 AM |
| Unoptimization | The **Unoptimization** job, which is a special job that should only be run manually, undoes the optimization done by deduplication and disables Data Deduplication for that volume. | [On-demand only](run#disabling-dedup) |

## Data Deduplication terminology

| Term | Definition |
| --- | --- |
| Chunk | A chunk is a section of a file that has been selected by the Data Deduplication chunking algorithm as likely to occur in other, similar files. |
| Chunk store | The chunk store is an organized series of container files in the System Volume Information folder that Data Deduplication uses to uniquely store chunks. |
| Dedup | An abbreviation for Data Deduplication that's commonly used in PowerShell, Windows Server APIs and components, and the Windows Server community. |
| File metadata | Every file contains metadata that describes interesting properties about the file that are not related to the main content of the file. For instance, Date Created, Last Read Date, Author, etc. |
| File stream | The file stream is the main content of the file. This is the part of the file that Data Deduplication optimizes. |
| File system | The file system is the software and on-disk data structure that the operating system uses to store files on storage media. Data Deduplication is supported on NTFS formatted volumes. |
| File system filter | A file system filter is a plugin that modifies the default behavior of the file system. To preserve access semantics, Data Deduplication uses a file system filter (Dedup.sys) to redirect reads to optimized content completely transparently to the user or application that makes the read request. |
| Optimization | A file is considered optimized (or deduplicated) by Data Deduplication if it has been chunked, and its unique chunks have been stored in the chunk store. |
| Optimization policy | The optimization policy specifies the files that should be considered for Data Deduplication. For example, files may be considered out-of-policy if they are brand new, open, in a certain path on the volume, or a certain file type. |
| Reparse point | A [reparse point](/en-us/windows/win32/fileio/reparse-points) is a special tag that notifies the file system to pass off I/O to a specified file system filter. When a file's file stream has been optimized, Data Deduplication replaces the file stream with a reparse point, which enables Data Deduplication to preserve the access semantics for that file. |
| Volume | A volume is a Windows construct for a logical storage drive that may span multiple physical storage devices across a one or more servers. Deduplication is enabled on a volume-by-volume basis. |
| Workload | A workload is an application that runs on Windows Server. Example workloads include general purpose file server, Hyper-V, and SQL Server. |

Warning

Unless instructed by authorized Microsoft Support Personnel, do not attempt to manually modify the chunk store. Doing so may result in data corruption or loss.

## Frequently asked questions

**How does Data Deduplication differ from other optimization products?** There are several important differences between Data Deduplication and other common storage optimization products:

- *How does Data Deduplication differ from Single Instance Store?* Single Instance Store, or SIS, is a technology that preceded Data Deduplication and was first introduced in Windows Storage Server 2008 R2. To optimize a volume, Single Instance Store identified files that were completely identical and replaced them with logical links to a single copy of a file that's stored in the SIS common store. Unlike Single Instance Store, Data Deduplication can get space savings from files that are not identical but share many common patterns and from files that themselves contain many repeated patterns. Single Instance Store was deprecated in Windows Server 2012 R2 and removed in Windows Server 2016 in favor of Data Deduplication.
- *How does Data Deduplication differ from NTFS compression?* NTFS compression is a feature of NTFS that you can optionally enable at the volume level. With NTFS compression, each file is optimized individually via compression at write-time. Unlike NTFS compression, Data Deduplication can get spacing savings across all the files on a volume. This is better than NTFS compression because files may have both internal duplication (which is addressed by NTFS compression) and have similarities with other files on the volume (which is not addressed by NTFS compression). Additionally, Data Deduplication has a post-processing model, which means that new or modified files will be written to disk unoptimized and will be optimized later by Data Deduplication.
- *How does Data Deduplication differ from archive file formats like zip, rar, 7z, cab, etc.?* Archive file formats, like zip, rar, 7z, cab, etc., perform compression over a specified set of files. Like Data Deduplication, duplicated patterns within files and duplicated patterns across files are optimized. However, you have to choose the files that you want to include in the archive. Access semantics are different, too. To access a specific file within the archive, you have to open the archive, select a specific file, and decompress that file for use. Data Deduplication operates transparently to users and administrators and requires no manual kick-off. Additionally, Data Deduplication preserves access semantics: optimized files appear unchanged after optimization.

**Can I change the Data Deduplication settings for my selected Usage Type?** Yes. Although Data Deduplication provides reasonable defaults for **Recommended workloads**, you might still want to tweak Data Deduplication settings to get the most out of your storage. Additionally, other workloads will [require some tweaking to ensure that Data Deduplication does not interfere with the workload](install-enable#enable-dedup-sometimes-considerations).

**Can I manually run a Data Deduplication job?** Yes, [all Data Deduplication jobs may be run manually](run#running-dedup-jobs-manually). This may be desirable if scheduled jobs did not run due to insufficient system resources or because of an error. Additionally, the Unoptimization job can only be run manually.

**Can I monitor the historical outcomes of Data Deduplication jobs?** Yes, [all Data Deduplication jobs make entries in the Windows Event Log](run#monitoring-dedup).

**Can I change the default schedules for the Data Deduplication jobs on my system?** Yes, [all schedules are configurable](advanced-settings#modifying-job-schedules). Modifying the default Data Deduplication schedules is particularly desirable to ensure that the Data Deduplication jobs have time to finish and do not compete for resources with the workload.