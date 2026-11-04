---
layout: Conceptual
title: Manage basic volumes | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/disk-management/manage-basic-volumes
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes basic disks and the requirements to add space to existing primary partitions and logical drives.
ms.date: 2023-03-08T00:00:00.0000000Z
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
locale: en-us
document_id: 8d3cc2b7-6449-bec4-3c25-bc010b776423
document_version_independent_id: adc141a5-67d0-f4a4-1736-efa02f85d149
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/disk-management/manage-basic-volumes.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/disk-management/manage-basic-volumes
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/disk-management/manage-basic-volumes.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 5f332dc7-bf70-dad9-efe2-38b9bab4ecd3
---

# Manage basic volumes | Microsoft Learn

> 
> \*\*

A basic disk is a physical disk that contains primary partitions, extended partitions, or logical drives. Partitions and logical drives on basic disks are called basic volumes. You can only create basic volumes on basic disks.

You can add more space to existing primary partitions and logical drives by extending them into adjacent, contiguous unallocated space on the same disk. To extend a basic volume, format it with the NTFS file system. You can extend a logical drive within contiguous free space in the extended partition that contains it. If you extend a logical drive beyond the free space available in the extended partition, the extended partition grows to contain the logical drive only if the extended partition is followed by contiguous unallocated space.