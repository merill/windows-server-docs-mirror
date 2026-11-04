---
layout: Conceptual
title: Network-Related Performance Counters | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/network-subsystem/net-sub-performance-counters
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn about the counters that are relevant to managing network performance.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-27T00:00:00.0000000Z
locale: en-us
document_id: 74c62d45-faca-7256-d5c7-392416b239d1
document_version_independent_id: 6c1b228d-7c27-2601-4289-86f8e5164ebe
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/network-subsystem/net-sub-performance-counters.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/network-subsystem/net-sub-performance-counters
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/network-subsystem/net-sub-performance-counters.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 4970a162-4255-6741-422c-69b0a7f66ea9
---

# Network-Related Performance Counters | Microsoft Learn

This topic lists the counters that are relevant to managing network performance, and contains the following sections.

- Resource Utilization
- Potential Network Problems
- Receive Side Coalescing (RSC) performance

## Resource Utilization

The following performance counters are relevant to network resource utilization.

- IPv4, IPv6

    - Datagrams Received/sec
    - Datagrams Sent/sec
- TCPv4, TCPv6

    - Segments Received/sec
    - Segments Sent/sec
    - Segments Retransmitted/sec
- Network Interface(\*), Network Adapter(\*)

    - Bytes Received/sec
    - Bytes Sent/sec
    - Packets Received/sec
    - Packets Sent/sec
    - Output Queue Length

        This counter is the length of the output packet queue (in packets). If this is longer than 2, delays occur. You should find the bottleneck and eliminate it if you can. Because NDIS queues the requests, this length should always be 0.
- Processor Information

    - % Processor Time
    - Interrupts/sec
    - DPCs Queued/sec

        This counter is an average rate at which DPCs were added to the logical processor's DPC queue. Each logical processor has its own DPC queue. This counter measures the rate at which DPCs are added to the queue, not the number of DPCs in the queue. It displays the difference between the values that were observed in the last two samples, divided by the duration of the sample interval.

## Potential Network Problems

The following performance counters are relevant to potential network problems.

- Network Interface(\*), Network Adapter(\*)

    - Packets Received Discarded
    - Packets Received Errors
    - Packets Outbound Discarded
    - Packets Outbound Errors
- WFPv4, WFPv6

    - Packets Discarded/sec
- UDPv4, UDPv6

    - Datagrams Received Errors
- TCPv4, TCPv6

    - Connection Failures
    - Connections Reset
- Network QoS Policy

    - Packets dropped
    - Packets dropped/sec
- Per Processor Network Interface Card Activity

    - Low Resource Receive Indications/sec
    - Low Resource Received Packets/sec
- Microsoft Winsock BSP

    - Dropped Datagrams
    - Dropped Datagrams/sec
    - Rejected Connections
    - Rejected Connections/sec

## Receive Side Coalescing (RSC) performance

The following performance counters are relevant to RSC performance.

- Network Adapter(\*)

    - TCP Active RSC Connections
    - TCP RSC Average Packet Size
    - TCP RSC Coalesced Packets/sec
    - TCP RSC Exceptions/sec

For links to all topics in this guide, see [Network Subsystem Performance Tuning](net-sub-performance-top).