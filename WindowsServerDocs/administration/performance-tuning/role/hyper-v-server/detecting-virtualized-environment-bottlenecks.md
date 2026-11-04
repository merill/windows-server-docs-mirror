---
layout: Conceptual
title: Detecting bottlenecks in a virtualized environment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/role/hyper-v-server/detecting-virtualized-environment-bottlenecks
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: How to detect and resolve potential Hyper-v performance bottlenecks
ms.topic: troubleshooting-general
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 75f80eed-c670-16ab-4865-726781b843c8
document_version_independent_id: 363a70fa-dc90-e59e-b549-90b2540c935b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/role/hyper-v-server/detecting-virtualized-environment-bottlenecks.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/role/hyper-v-server/detecting-virtualized-environment-bottlenecks
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/role/hyper-v-server/detecting-virtualized-environment-bottlenecks.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 2265bea4-0fe8-0a3b-0c64-6275e36836ed
---

# Detecting bottlenecks in a virtualized environment | Microsoft Learn

This section should give you some hints on what to monitor by using Performance Monitor and how to identify where the problem might be when either the host or some of the virtual machines do not perform as you would have expected.

## Processor bottlenecks

Here are some common scenarios that could cause processor bottlenecks:

- One or more logical processors are loaded
- One or more virtual processors are loaded

You can use the following performance counters from the host:

- Logical Processor Utilization - \Hyper-V Hypervisor Logical Processor(\*)\% Total Run Time
- Virtual Processor Utilization - \Hyper-V Hypervisor Virtual Processor(\*)\% Total Run Time
- Root Virtual Processor Utilization - \Hyper-V Hypervisor Root Virtual Processor(\*)\% Total Run Time

If the **Hyper-V Hypervisor Logical Processor(\_Total)\% Total Runtime** counter is over 90%, the host is overloaded. You should add more processing power or move some virtual machines to a different host.

If the **Hyper-V Hypervisor Virtual Processor(VM Name:VP x)\% Total Runtime** counter is over 90% for all virtual processors, you should do the following:

- Verify that the host is not overloaded
- Find out if the workload can leverage more virtual processors
- Assign more virtual processors to the virtual machine

If **Hyper-V Hypervisor Virtual Processor(VM Name:VP x)\% Total Runtime** counter is over 90% for some, but not all, of the virtual processors, you should do the following:

- If your workload is receive network-intensive, you should consider using vRSS.
- If the virtual machines are not running Windows Server 2012 R2, you should add more network adapters.
- If your workload is storage-intensive, you should enable virtual NUMA and add more virtual disks.

If the **Hyper-V Hypervisor Root Virtual Processor (Root VP x)\% Total Runtime** counter is over 90% for some, but not all, virtual processors and the **Processor (x)\% Interrupt Time and Processor (x)\% DPC Time** counter approximately adds up to the value for the **Root Virtual Processor(Root VP x)\% Total Runtime** counter, you should ensure enable VMQ on the network adapters.

## Memory bottlenecks

Here are some common scenarios that could cause memory bottlenecks:

- The host is not responsive.
- Virtual machines cannot be started.
- Virtual machines run out of memory.

You can use the following performance counters from the host:

- Memory\Available Mbytes
- Hyper-V Dynamic Memory Balancer (\*)\Available Memory

You can use the following performance counters from the virtual machine:

- Memory\Available Mbytes

If the **Memory\Available Mbytes** and **Hyper-V Dynamic Memory Balancer (\*)\Available Memory** counters are low on the host, you should stop non-essential services and migrate one or more virtual machines to another host.

If the **Memory\Available Mbytes** counter is low in the virtual machine, you should assign more memory to the virtual machine. If you are using Dynamic Memory, you should increase the maximum memory setting.

## Network bottlenecks

Here are some common scenarios that could cause network bottlenecks:

- The host is network bound.
- The virtual machine is network bound.

You can use the following performance counters from the host:

- Network Interface(*network adapter name*)\Bytes/sec

You can use the following performance counters from the virtual machine:

- Hyper-V Virtual Network Adapter (*virtual machine name name&lt;GUID&gt;*)\Bytes/sec

If the **Physical NIC Bytes/sec** counter is greater than or equal to 90% of capacity, you should add additional network adapters, migrate virtual machines to another host, and configure Network QoS.

If the **Hyper-V Virtual Network Adapter Bytes/sec** counter is greater than or equal to 250 MBps, you should add additional teamed network adapters in the virtual machine, enable vRSS, and use SR-IOV.

If your workloads can't meet their network latency, enable SR-IOV to present physical network adapter resources to the virtual machine.

## Storage bottlenecks

Here are some common scenarios that could cause storage bottlenecks:

- The host and virtual machine operations are slow or time out.
- The virtual machine is sluggish.

You can use the following performance counters from the host:

- Physical Disk(*disk letter*)\Avg. disk sec/Read
- Physical Disk(*disk letter*)\Avg. disk sec/Write
- Physical Disk(*disk letter*)\Avg. disk read queue length
- Physical Disk(*disk letter*)\Avg. disk write queue length

If latencies are consistently greater than 50ms, you should do the following:

- Spread virtual machines across additional storage
- Consider purchasing faster storage
- Consider Tiered Storage Spaces, which was introduced in Windows Server 2012 R2
- Consider using Storage QoS, which was introduced in Windows Server 2012 R2
- Use VHDX

## Additional References

- [Hyper-V terminology](terminology)
- [Hyper-V architecture](architecture)
- [Hyper-V server configuration](configuration)
- [Hyper-V processor performance](processor-performance)
- [Hyper-V memory performance](memory-performance)
- [Hyper-V storage I/O performance](storage-io-performance)
- [Hyper-V network I/O performance](network-io-performance)
- [Linux Virtual Machines](linux-virtual-machine-considerations)