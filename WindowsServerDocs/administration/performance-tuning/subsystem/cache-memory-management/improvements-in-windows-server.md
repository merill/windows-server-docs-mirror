---
layout: Conceptual
title: Cache and Memory Manager Improvements | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/subsystem/cache-memory-management/improvements-in-windows-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Cache and Memory Manager Improvements in Windows Server 2016
ms.topic: whats-new
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ab9aa920-d7f0-ec41-157f-b36f8a5088a8
document_version_independent_id: 8625446a-bcee-a695-c1a9-7d170e96565e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/subsystem/cache-memory-management/improvements-in-windows-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/subsystem/cache-memory-management/improvements-in-windows-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/subsystem/cache-memory-management/improvements-in-windows-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f9cf537e-3e5a-4f31-a8e2-d06c28985eda
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6c57776-ab71-4356-880c-c5ff411d7fe1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b0200c40-0bea-4a73-a79b-8c68e19d3d16
- https://authoring-docs-microsoft.poolparty.biz/devrel/e2d3fbf8-36df-4730-9ac5-e1c53887f039
platformId: f2255959-e7d3-b906-c771-875cd1f82cf9
---

# Cache and Memory Manager Improvements | Microsoft Learn

This topic describes Cache Manager and Memory Manager improvements in Windows Server 2012 and 2016.

## Cache Manager improvements in Windows Server 2022

Cache manager is now NUMA aware, which ensures the system is better at avoiding data movement across NUMA boundaries. Avoiding accesses from a NUMA node to memory and other kernel resources on another NUMA node adds a lot of overhead. By making Cache manager NUMA aware, we have eliminated such cross-NUMA hops, thus optimizing cached IO workloads running on multi node configurations.

## Cache Manager improvements in Windows Server 2019

We added Zero-Copy support for Persistent Memory (PMEM) Storage. For more information on persistent memory, see [Understand and deploy persistent memory](/en-us/azure/azure-local/concepts/deploy-persistent-memory). In Direct Access (DAX) mode, PMEM operates like memory to get the lowest latency, wherein we eliminate an extra copy of data and bypass a lot of overhead from Filesystem Mini-Filters and the storage stack. This mode only works with NTFS as a filesystem.

## Cache Manager improvements in Windows Server 2016

Cache Manager also added support for true Asynchronous Cached Reads. This could potentially improve the performance of an application if it relies heavily on asynchronous cached reads. While most in-box filesystems have supported async-cached reads for a while, there were often performance limitations due to various design choices related to handling of thread-pools and filesystems' internal work queues. With support from kernel-proper, Cache Manager now hides all the thread-pool and work queue management complexities from filesystems making it more efficient at handling asynchronous cached reads. Cache Manager has one set of control data structures for each of (system supported maximum) VHD-nesting levels to maximize parallelism.

## Cache Manager improvements in Windows Server 2012

In addition to Cache Manager enhancements to read ahead logic for sequential workloads, a new API [CcSetReadAheadGranularityEx](/en-us/windows-hardware/drivers/ifs/ccsetreadaheadgranularityex) was added to let file system drivers, such as SMB, change their read ahead parameters. It allows better throughput for remote file scenarios by sending multiple small-sized read ahead requests instead of sending a single large read ahead request. Only kernel components, such as file system drivers, can programmatically configure these values on a per-file basis.

## Memory Manager improvements in Windows Server 2012

Enabling page combining may reduce memory usage on servers, which have a lot of private, pageable pages with identical contents. For example, servers running multiple instances of the same memory-intensive app, or a single app that works with highly repetitive data, might be good candidates to try page combining. The downside of enabling page combining is increased CPU usage.

Here are some examples of server roles where page combining is unlikely to give much benefit:

- File servers (most of the memory is consumed by file pages which are not private and therefore not combinable)
- Microsoft SQL Servers that are configured to use AWE or large pages (most of the memory is private but non-pageable)

Page combining is disabled by default but can be enabled by using the [Enable-MMAgent](/en-us/powershell/module/mmagent/enable-mmagent) Windows PowerShell cmdlet. Page combining was added in Windows Server 2012.