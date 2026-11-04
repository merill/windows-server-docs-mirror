---
layout: Conceptual
title: Remote Desktop Services - GPU acceleration | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-graphics-virtualization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to plan information to help you choose the right graphics virtualization option for your RDS deployment.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: concept-article
author: robinharwood
locale: en-us
document_id: c73065c6-f9e6-466d-a78f-21bb03b2788a
document_version_independent_id: d1df688d-b858-7100-0125-280389501ead
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-graphics-virtualization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-graphics-virtualization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-graphics-virtualization.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 58135667-e417-c1b3-c367-13e2cfc969af
---

# Remote Desktop Services - GPU acceleration | Microsoft Learn

Remote Desktop Services (RDS) works with native graphics acceleration and the graphics virtualization technologies supported by Windows Server. For information on those technologies, their differences, and how to deploy them, see [Plan for GPU acceleration in Windows Server](../../virtualization/hyper-v/plan/plan-for-gpu-acceleration-in-windows-server).

When you plan for graphics acceleration in your RDS environment, your choice of user scale and user workloads drives which graphics rendering technology you use:

![Diagram that compares user scale and GPU requirements to determine the best GPU technology for your environment.](media/rds-gpu.png)