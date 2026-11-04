---
layout: Conceptual
title: Insider preview for Windows Time Service features in Windows Server 2019 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/windows-time-service/insider-preview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: New Windows Time Service features in Windows Server 2019
author: robinharwood
ms.author: roharwoo
ms.date: 2021-11-04T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 70b7797e-f018-e538-1a51-dd6ca694b436
document_version_independent_id: ad75618a-360a-b81e-ffab-2a62155335bc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/windows-time-service/insider-preview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/windows-time-service/insider-preview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/windows-time-service/insider-preview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 5f9d295e-06ea-c1bf-facb-6bb3824b789d
---

# Insider preview for Windows Time Service features in Windows Server 2019 | Microsoft Learn

## Leap second support

A leap second is an occasional 1-second adjustment to UTC. As the earth's rotation slows, [UTC](https://en.wikipedia.org/wiki/Coordinated_Universal_Time) (an atomic timescale) diverges from [mean solar time](https://en.wikipedia.org/wiki/Solar_time#Mean_solar_time) or astronomical time. Once UTC has diverged by at most .9 seconds, a [leap second](https://en.wikipedia.org/wiki/Leap_second) is inserted to keep UTC in-sync with mean solar time.

Leap seconds have become important to meet the accuracy and traceability regulatory requirements both in the United States and the European Union.

For more information, see:

- Our [announcement blog](https://techcommunity.microsoft.com/t5/networking-blog/top-10-networking-features-in-windows-server-2019-10-accurate/ba-p/339739/)
- Validation Guide for the [Developers](https://aka.ms/Dev-LeapSecond)
- Validation Guide for the [IT Pro](https://aka.ms/ITPro-LeapSecond)

## Precision time protocol

A new time provider included in Windows Server 2019 and Windows 10 (version 1809) allows you to synchronize time using the Precision Time Protocol (PTP). As time distributes across a network, it encounters delay (latency), which if not accounted for, or if it is not symmetric, it becomes increasingly difficult to understand the time-stamp sent from the time server. PTP enables network devices to add the latency introduced by each network device into the timing measurements thereby providing a far more accurate time sample to the windows client.

For more information, see:

- Our [announcement blog](https://techcommunity.microsoft.com/t5/networking-blog/top-10-networking-features-in-windows-server-2019-10-accurate/ba-p/339739/)
- Validation Guide for the [IT Pro](https://aka.ms/PTPValidation)

## Software timestamping

When receiving a timing packet over the network from a time server, it must be processed by the operating system's networking stack before being consumed in the time service. Each component in the networking stack introduces a variable amount of latency that affects the accuracy of the timing measurement.

![software timestamping](../media/windows-time-service/software-timestamping.png)

To address this problem, software timestamping allows us to timestamp packets before and after the "Windows Networking Components" shown above to account for the delay in the operating system.

For more information, see:

- Our [announcement blog](https://techcommunity.microsoft.com/t5/networking-blog/top-10-networking-features-in-windows-server-2019-10-accurate/ba-p/339739/)
- [Validation Guides for Developers and IT Pros](https://github.com/microsoft/W32Time/tree/master/Leap%20Seconds)