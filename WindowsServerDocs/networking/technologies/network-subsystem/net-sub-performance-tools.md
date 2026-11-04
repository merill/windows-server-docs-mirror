---
layout: Conceptual
title: Performance Tools for Network Workloads | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/network-subsystem/net-sub-performance-tools
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn about performance tools including the Client to Server Traffic tool and TCP/IP Window Size.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-27T00:00:00.0000000Z
locale: en-us
document_id: dca49010-a098-e6d6-f877-939967f40230
document_version_independent_id: 19a38737-9fe5-dd65-3b2f-042e3bbe37c3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/network-subsystem/net-sub-performance-tools.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/network-subsystem/net-sub-performance-tools
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/network-subsystem/net-sub-performance-tools.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 52be5826-bab0-7132-1b85-10ed80bf11cb
---

# Performance Tools for Network Workloads | Microsoft Learn

You can use this topic to learn about performance tools.

This topic contains sections about the Client to Server Traffic tool and TCP/IP Window Size.

## Client to Server Traffic tool

The Client to Server Traffic (ctsTraffic) tool provides you with the ability to create and verify network traffic.

For more information, and to download the tool, see [ctsTraffic (Client-To-Server Traffic)](https://github.com/Microsoft/ctsTraffic).

## TCP/IP Window Size

For 1 GB adapters, the settings shown in the previous table should provide good throughput because NTttcp sets the default TCP window size to 64 K through a specific logical processor option (SO\_RCVBUF) for the connection. This provides good performance on a low-latency network.

In contrast, for high-latency networks or for 10 GB adapters, the default TCP window size value for NTttcp yields less than optimal performance. In both cases, you must adjust the TCP window size to allow for the larger bandwidth delay product.

You can statically set the TCP window size to a large value by using the **-rb** option. This option disables TCP Window Auto-Tuning, and we recommend using it only if the user fully understands the resultant change in TCP/IP behavior. By default, the TCP window size is set at a sufficient value and adjusts only under heavy load or over high-latency links.

For more information, see [Network Subsystem Performance Tuning](net-sub-performance-top).