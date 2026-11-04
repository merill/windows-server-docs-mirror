---
layout: Conceptual
title: Manage disks | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/disk-management/manage-disks
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how to manage disks in a computer using Disk Management and discover whether a disk is online or offline and how to bring it online.
ms.date: 2023-03-08T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: daa59f03-1cff-49c0-a7ac-7a8832c8b196
document_version_independent_id: df6bab15-456c-87e7-d2eb-58ae167f9d59
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/disk-management/manage-disks.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/disk-management/manage-disks
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/disk-management/manage-disks.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c52803c5-e0f5-482c-2fb8-8a7249d91d0e
---

# Manage disks | Microsoft Learn

This article and the related topics show you how to use Disk Management to manage the disks in a computer. It includes information about how Windows manages the online status of new disks.

## Online and offline status

Disk Management displays whether a disk is online (available) or offline.

- In Windows, by default, all newly discovered disks are brought online with read and write access.
- In Windows Server, by default, newly discovered disks are brought online with read and write access unless they're on a shared bus (such as SCSI, iSCSI, Serial Attached SCSI, or Fibre Channel). Disks on a shared bus are offline the first time they're detected.

If a disk is offline, you must bring it online before you can initialize it or create volumes on it.

To bring a disk online or take it offline, follow these steps.

1. Open Disk Management. In the search box on the taskbar, enter **Computer Management** and select **Storage** &gt; **Disk Management**.
2. Right-click the disk name, then select the appropriate action.