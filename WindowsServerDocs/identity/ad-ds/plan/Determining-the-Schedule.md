---
layout: Conceptual
title: Determining the Schedule | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/determining-the-schedule
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Determining the Schedule'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: b4377629-f50c-d73b-41a9-a3645493fb52
document_version_independent_id: e77d3409-7465-e571-c3cf-e6a4dc23d54d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Determining-the-Schedule.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/determining-the-schedule
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Determining-the-Schedule.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 0f6968e8-7c50-47db-7300-22e951950618
---

# Determining the Schedule | Microsoft Learn

You can control site link availability by setting a schedule for site links. When replication between two sites traverses multiple site links, the intersection of the replication schedules on all the relevant links determines the connection schedule between the two sites.

To plan for setting the site link schedule, create two overlapping schedules between site links that contain domain controllers that directly replicate with each other. Use the default (100-percent available) schedule on those links unless you want to block replication traffic during peak hours. By blocking replication, you give priority to other traffic, but you also increase replication latency.

Domain controllers store time in Coordinated Universal Time (UTC). Time settings in site link object schedules conform to the local time of the site and computer on which the schedule is set. When a domain controller contacts a computer that is in a different site and time zone, the schedule on the domain controller displays the time setting according to the local time for the site of the computer.