---
layout: Conceptual
title: Network guidelines | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/network-guidance
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Bandwidth recommendations for Remote Desktop deployments.
author: robinharwood
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: best-practice
ms.author: roharwoo
locale: en-us
document_id: 91116801-9136-ee05-969e-6f90d6a48c79
document_version_independent_id: d63869fe-cbb6-4517-4a56-e0bc85746682
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/network-guidance.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/network-guidance
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/network-guidance.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 92373688-33d5-7e77-9a24-5c74e7fb83a0
---

# Network guidelines | Microsoft Learn

When using a remote Windows session, your network's available bandwidth greatly impacts the quality of your experience. Different applications and display resolutions require different network configurations, so it's important to make sure your network is configured to meet your needs.

Note

The following recommendations apply to networks with less than 0.1% loss. These recommendations apply regardless of how many sessions you're hosting on your virtual machines (VMs).

## Applications

The following table lists the minimum recommended bandwidths for a smooth user experience. These recommendations are based on the guidelines in [Remote Desktop workloads](remote-desktop-workloads).

| Workload type | Recommended bandwidth |
| --- | --- |
| Light | 1.5 Mbps |
| Medium | 3 Mbps |
| Heavy | 5 Mbps |
| Power | 15 Mbps |

Keep in mind that the stress put on your network depends on both your app workload's output frame rate and your display resolution. If either the frame rate or display resolution increases, the bandwidth requirement will also rise. For example, a light workload with a high-resolution display requires more available bandwidth than a light workload with regular or low resolution.

Other scenarios can have their bandwidth requirements change depending on how you use them, such as:

- Voice or video conferencing
- Real-time communication
- Streaming 4K video

Make sure to load test these scenarios in your deployment using simulation tools like Login VSI. Vary the load size, run stress tests, and test common user scenarios in remote sessions to better understand your network's requirements.

## Display resolutions

Different display resolutions require different available bandwidths. The following table lists the bandwidths we recommend for a smooth user experience at typical display resolutions with a frame rate of 30 frames per second (fps). These recommendations apply to single and multiple user scenarios. Keep in mind that scenarios involving a frame rate under 30 fps, such as reading static text, require less available bandwidth.

| Typical display resolutions at 30 fps | Recommended bandwidth |
| --- | --- |
| About 1024 × 768 px | 1.5 Mbps |
| About 1280 × 720 px | 3 Mbps |
| About 1920 × 1080 px | 5 Mbps |
| About 3840 × 2160 px (4K) | 15 Mbps |

## Azure Virtual Desktop experience estimator

The Azure region you're in can affect user experience as much as network conditions. Check out the [Azure Virtual Desktop experience estimator](https://azure.microsoft.com/services/virtual-desktop/assessment/) to learn more.

## Assistive technologies

Assistive technology workloads, like using Narrator in the remote session, require connections with a connection round trip time (RTT) of 20 milliseconds (ms) or better for the best user experience.