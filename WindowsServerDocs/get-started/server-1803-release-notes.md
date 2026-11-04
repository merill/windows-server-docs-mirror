---
layout: Conceptual
title: Release Notes - Important Issues in Windows Server, version 1803 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/server-1803-release-notes
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Learn about any known issues, limitations, or other information you need before you install Windows Server, version 1803
ms.date: 2018-05-07T00:00:00.0000000Z
ms.topic: release-notes
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: cfaa1497-7893-889a-7cd4-a88a8b11c005
document_version_independent_id: 46ff40e0-a9f4-fbe1-434e-afa94e757b94
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/server-1803-release-notes.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/server-1803-release-notes
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/server-1803-release-notes.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 94755930-ba02-04df-b031-db7d6bb8d319
---

# Release Notes - Important Issues in Windows Server, version 1803 | Microsoft Learn

> 
> Applies to: Windows Server Semi-Annual Channel

These release notes summarize the most critical issues in the Windows Server operating system, including ways to avoid or work around known issues. To learn about new features in this release, see [What's New in Windows Server version 1803](whats-new-in-windows-server-1803). Check out [About Windows containers](/en-us/virtualization/windowscontainers/about/) if you're interested in running a Windows Server, version 1803, container.

Unless otherwise specified, each reported issue applies to all editions and installation options of Windows Server, version 1803.

We continuously update this article. If any known issues are identified, we'll document them here.

## Software-defined datacenter

Software-defined datacenter features like Storage Spaces Direct, software-defined networking, and shielded virtual machines aren't included in Windows Server, version 1803. As described in [Windows Server Semi-Annual Channel update](https://cloudblogs.microsoft.com/windowsserver/2018/03/29/windows-server-semi-annual-channel-update/), the Semi-Annual Channel of Windows Server is focused on containers and application scenarios that benefit from faster innovation.

If you need infrastructure roles, use a Long-Term Servicing Channel release: Windows Server 2016 (available now) or [Windows Server 2019](https://cloudblogs.microsoft.com/windowsserver/2018/03/20/introducing-windows-server-2019-now-available-in-preview) (coming later this year).

We're committed to building the best platform for hyper-converged infrastructure, and we continue to develop new features and improve existing ones based on your feedback. Thank you for helping us get to [10,000+ clusters of Storage Spaces Direct](https://techcommunity.microsoft.com/t5/storage-at-microsoft/storage-spaces-direct-10-000-clusters-and-counting/ba-p/428185)! We look forward to sharing more later this year.