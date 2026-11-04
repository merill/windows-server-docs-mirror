---
layout: Conceptual
title: Hyper-V processor performance | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/role/hyper-v-server/processor-performance
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Learn about the processor performance considerations to use for tuning and improving Hyper-V performance.
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2025-01-17T00:00:00.0000000Z
locale: en-us
document_id: 4f64afc3-8818-4154-fc30-8dab30036bc1
document_version_independent_id: 2f57682a-ad67-3753-9a50-fa5f7dbc1cb5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/role/hyper-v-server/processor-performance.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/role/hyper-v-server/processor-performance
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/role/hyper-v-server/processor-performance.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6b3dc07a-443c-0473-6b6e-a69397a48774
---

# Hyper-V processor performance | Microsoft Learn

Virtualization servers host multiple virtual machines (VMs) that are isolated from each other but share underlying hardware resources. The processors, memory, and I/O devices are virtualized. When you consolidate servers onto a single machine, virtualization improves resource usage, improves energy efficiency, and reduces the servers' operational and maintenance costs. This article helps you understand the processor performance considerations for fine-tuning and improving Hyper-V performance.

## Virtual machine integration services

The virtual machine (VM) integration services include enlightened drivers for the Hyper-V-specific I/O devices, which significantly reduce CPU overhead for I/O compared to emulated devices. Install the latest version of the VM integration services in every supported VM. The services decrease the CPU usage of the guests, from idle guests to heavy-use guests, and improves the I/O throughput. This step is the first one in tuning performance in a server running Hyper-V. For a list of supported guest operating systems, see [Hyper-V overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531%28v=ws.11%29).

## Virtual processors

Assess your workload to determine the processor requirements to avoid under or over provisioning. Use the results of your assessment to configure number of virtual processors required. Increase the number of virtual processors if the VM requires more processing resources under peak load. To learn more about the maximum configurable components in Hyper-V, see [Plan for Hyper-V scalability in Windows Server](../../../../virtualization/hyper-v/maximum-scale-limits).

When using Simultaneous multithreading (SMT), we recommended using virtual processors in multiples of two. Most modern AMD and Intel based systems have SMT enabled, where enabled we recommended configuring virtual machines to have an even number of virtual processors. To learn more about SMT, see [Manage Hyper-V hypervisor scheduler types](../../../../virtualization/hyper-v/manage/manage-hyper-v-scheduler-types).

## Background activity

Minimizing the background activity in idle VMs releases CPU cycles that other VMs use. Windows guests typically use less than one percent of a CPU when they're idle. The following are best practices to minimize background CPU usage of a VM:

- Install the latest version of the VM integration services.
- Remove the emulated network adapter through the VM settings dialog box (use the Microsoft Hyper-V-specific adapter).
- Remove unused devices such as the CD-ROM and COM port, or disconnect their media.
- Keep the Windows guest operating system on the sign-in screen when it isn't being used and disable the screen saver.
- Review the scheduled tasks and services that are enabled by default.
- Review the Event Tracing for Windows (ETW) trace providers that are on by default by running `logman.exe query -ets`.
- Improve server applications to reduce periodic activity (such as timers).
- Close Server Manager on both the host and guest operating systems.
- Don't leave Hyper-V Manager running since it constantly refreshes the VM's thumbnail.

The following are best practices for configuring a *client version* of Windows in a VM to reduce the overall CPU usage:

- Disable background services such as SuperFetch and Windows Search.
- Disable scheduled tasks such as scheduled defrag.

## Virtual NUMA

Hyper-V in Windows Server expands VM scale limits to enable virtualizing large scale-up workloads. When you create large VMs, memory from multiple NUMA nodes on the host system are typically used. In that type of VM configuration, if you don't allocate virtual processors and memory from the same NUMA node, workloads might have poor performance. Performance is negatively affected because workloads can't take advantage of the NUMA optimizations. To learn more about the maximum configurable components in Hyper-V, see [Plan for Hyper-V scalability in Windows Server](../../../../virtualization/hyper-v/maximum-scale-limits).

In Windows Server, Hyper-V presents a Virtual NUMA topology to VMs. By default, this Virtual NUMA topology is optimized to match the NUMA topology of the underlying host computer. Exposing a Virtual NUMA topology into a VM lets the guest operating system, and any NUMA-aware applications running within it, take advantage of the NUMA performance optimizations, just as they would when running on a physical computer.

There's no distinction between a virtual and a physical NUMA from the workload's perspective. Inside a VM, when a workload allocates local memory for data, and accesses that data in the same NUMA node, fast local memory access results on the underlying physical system. Performance penalties due to remote memory access are successfully avoided. Only NUMA-aware applications can benefit from vNUMA.

Microsoft SQL Server is an example of NUMA-aware application. For more information, see [Understanding nonuniform memory access](/en-us/previous-versions/sql/sql-server-2008-r2/ms178144%28v=sql.105%29).

You can't use Virtual NUMA and dynamic memory features at the same time. A VM with dynamic memory enabled on it effectively has only one Virtual NUMA node. And no NUMA topology is presented to the VM regardless of the Virtual NUMA settings.

For more info on Virtual NUMA, see [Hyper-V Virtual NUMA overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282282%28v=ws.11%29).

## Related links

Here are some articles to help you learn more about Hyper-V.

- [Plan for Hyper-V scalability in Windows Server](../../../../virtualization/hyper-v/maximum-scale-limits)
- [Hyper-V architecture](architecture)
- [Hyper-V server configuration](configuration)
- [Hyper-V memory performance](memory-performance)
- [Hyper-V storage I/O performance](storage-io-performance)
- [Hyper-V network I/O performance](network-io-performance)
- [Detecting bottlenecks in a virtualized environment](detecting-virtualized-environment-bottlenecks)
- [Linux VMs](linux-virtual-machine-considerations)