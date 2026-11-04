---
layout: Conceptual
title: Determining the Cost | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/determining-the-cost
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn more about assigning cost values to links
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 2da675b3-12fe-d5bf-49a1-48a4aefc589b
document_version_independent_id: f41cc4a1-c89d-fd85-d9d5-2b954af31d0e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Determining-the-Cost.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/determining-the-cost
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Determining-the-Cost.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 7b28a833-dfc8-18b3-e4ce-ad0f5bd52c99
---

# Determining the Cost | Microsoft Learn

You assign cost values to site links to favor inexpensive connections over expensive connections. Certain applications and services, such as Domain Controller Locator (DCLocator) and Distributed File System Namespaces (DFSN), also use cost information to locate the nearest resources. Site link cost can be used to determine which domain controller is contacted by clients in one site if the domain controller for the specified domain doesn't exist at that site. The client contacts the domain controller by using the site link that has the lowest cost assigned to it.

We recommend that the cost value be defined on a site-wide basis. Cost is usually based not only on the total bandwidth of the link but also on the availability, latency, and monetary cost of the link.

To determine the costs to place on site links, document the connection speed for each site link. Refer to the "Geographic Locations and Communication Links" (DSSTOPO\_1.doc) worksheet in [Collecting Network Information](collecting-network-information) for information about the connection speed that you identified.

The following table lists the speeds for different types of networks.

| Network type | Speed |
| --- | --- |
| Very slow | 56 kilobits per second (Kbps) |
| Slow | 64 Kbps |
| Integrated Services Digital Network (ISDN) | 64 Kbps or 128 Kbps |
| Frame relay | Variable rate, commonly between 56 Kbps and 1.5 megabits per second (Mbps) |
| T1 | 1.5 Mbps |
| T3 | 45 Mbps |
| 10BaseT | 10 Mbps |
| Asynchronous transfer mode (ATM) | Variable rate, commonly between 155 Mbps and 622 Mbps |
| 100BaseT | 100 Mbps |
| Gigabit Ethernet | 1 gigabit per second (Gbps) |

Use the following table to calculate the cost of each site link based on wide area network speed (WAN) link speed. For WAN link speed that isn't listed in the table, you can calculate a relative cost factor by dividing 1,024 by the logarithm of the available bandwidth, as measured in Kbps.

| Available bandwidth (Kbps) | Cost |
| --- | --- |
| 9.6 | 1,042 |
| 19.2 | 798 |
| 38.4 | 644 |
| 56 | 586 |
| 64 | 567 |
| 128 | 486 |
| 256 | 425 |
| 512 | 378 |
| 1,024 | 340 |
| 2,048 | 309 |
| 4,096 | 283 |

These costs don't reflect differences in reliability between network links. Set higher costs on any failure-prone network links so that you don't have to rely on those links for replication. By setting higher site link costs, you can control replication failover when a site link fails.