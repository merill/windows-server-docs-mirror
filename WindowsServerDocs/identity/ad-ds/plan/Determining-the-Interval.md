---
layout: Conceptual
title: Determining the Interval | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/determining-the-interval
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Determining the Interval'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 6e37be4a-764f-21bd-32f4-f7f6dfa2c4a5
document_version_independent_id: ae59e355-fb1d-150c-1293-c95c48253d44
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Determining-the-Interval.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/determining-the-interval
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Determining-the-Interval.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d71a308a-ef60-4a97-94d8-dbe8766909af
---

# Determining the Interval | Microsoft Learn

You must set the site link replication interval property to indicate how frequently you want replication to occur during the times when the schedule allows replication. For example, if the schedule allows replication between 02:00 hours and 04:00 hours, and the replication interval is set for 30 minutes, replication can occur up to four times during the scheduled time. The default replication interval is 180 minutes, or 3 hours. The minimum interval is 15 minutes.

Consider the following criteria to determine how often replication occurs within the schedule window:

- A small interval decreases latency but increases the amount of wide area network (WAN) traffic.
- To keep domain directory partitions up to date, low latency is preferred.

With a store-and-forward replication strategy, it is difficult to determine just how long a directory update might take to be replicated to every domain controller. To provide a conservative estimate of maximum latency, perform these tasks:

- Create a table of all the sites on your network, as shown in the following example:

    | Sites | Seattle | Boston | Los Angeles | New York | Washington, D.C. |
    | --- | --- | --- | --- | --- | --- |
    | Seattle | 0.25 |  |  |  |  |
    | Boston |  | 0.25 |  |  |  |
    | Los Angeles |  |  | 0.25 |  |  |
    | New York |  |  |  | 0.25 |  |
    | Washington, D.C. |  |  |  |  | 0.25 |

    A worst-case latency within a site is estimated to be 15 minutes.
- From the replication schedule, determine the maximum replication latency that is possible on any site link that connects two hub sites.

    For example, if replication occurs between Seattle and New York every three hours, the maximum delay for replication between these sites is three hours. If the replication delay between New York and Seattle is the longest scheduled delay among all hub sites, the maximum latency between all hubs is three hours.
- For each hub site, create a table of the maximum latencies between the hub site and any of its satellite sites.

    For example, if replication occurs between New York and Washington, D.C., every four hours and this is the longest replication delay between New York and any of its satellite sites, the maximum latency between New York and its satellites is four hours.
- Combine these maximum latencies to determine the maximum latency for the entire network.

    For example, if the maximum latency between Seattle and its satellite site in Los Angeles is one day, the maximum replication latency for this set of links (Washington, D.C.-New York-Seattle-Los Angeles) is 31 hours, that is, 4 (Washington, D.C.-New York) + 3 (New York-Seattle) + 24 (Seattle-Los Angeles), as shown in the following table.

    | Sites | Seattle | Boston | Los Angeles | New York | Washington, D.C. |
    | --- | --- | --- | --- | --- | --- |
    | Seattle | 0.25 | 4+3 | 24.00 | 3.00 | 4+3 |
    | Boston |  | 0.25 | 4+3+24 | 4.00 | 4.00 |
    | Los Angeles |  |  | 0.25 | 24 + 3 | 24+3+4 |
    | New York |  |  |  | 0.25 | 4.00 |
    | Washington, D.C. |  |  |  |  | 0.25 |