---
layout: Conceptual
title: Setting Site Link Properties | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/setting-site-link-properties
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Setting Site Link Properties'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 228ab2a2-b781-3bae-62ba-c1b1aa2adbd1
document_version_independent_id: a9d3eba2-22ae-f1f8-27aa-258d1fd58af7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Setting-Site-Link-Properties.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/setting-site-link-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Setting-Site-Link-Properties.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 8d912ab7-21d9-816d-54dc-434479b22480
---

# Setting Site Link Properties | Microsoft Learn

Intersite replication occurs according to the properties of the connection objects. When the Knowledge Consistency Checker (KCC) creates connection objects, it derives the replication schedule from properties of the site link objects. Each site link object represents the wide area network (WAN) connection between two or more sites.

Setting site link object properties includes the following steps:

- Determining the cost that is associated with that replication path. The KCC uses cost to determine the least expensive route for replication between two sites that replicate the same directory partition.
- Determining the schedule that defines the times during which intersite replication can occur.
- Determining the replication interval that defines how frequently replication should occur during the times when replication is allowed, as defined in the schedule.

## In this guide

- [Determining the Cost](determining-the-cost)
- [Determining the Schedule](determining-the-schedule)
- [Determining the Interval](determining-the-interval)