---
layout: Conceptual
title: Apply a quota to a volume or folder | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/checklist-apply-quota-to-volume-or-folder
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to apply a storage quota to a volume or folder
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: checklist
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: e6781683-609c-43ae-89b8-b196b4b2dfc9
document_version_independent_id: 66beb5d4-0f73-e298-f9a5-abba4fdd93d9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/checklist-apply-quota-to-volume-or-folder.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/checklist-apply-quota-to-volume-or-folder
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/checklist-apply-quota-to-volume-or-folder.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e88197d3-2115-4c1b-67d9-972fde6c3f2d
---

# Apply a quota to a volume or folder | Microsoft Learn

1. Configure e-mail settings if you plan to send threshold notifications or storage reports by e-mail. [Configure E-Mail Notifications](configure-email-notifications)
2. Assess storage requirements on the volume or folder. You can use reports on the **Storage Reports Management** node to provide data. (For example, run a Files by Owner report on demand to identify users who use large amounts of disk space.) [Generate Reports on Demand](generate-reports-on-demand)
3. Review available pre-configured quota templates. (In **Quota Management**, click the **Quota Templates** node.) [Edit Quota Template Properties](edit-quota-template-properties)-Or-  Create a new quota template to enforce a storage policy in your organization. [Create a Quota Template](create-quota-template)
4. Create a quota based on the template on the volume or folder. [Create a Quota](create-quota) -Or-  Create an auto apply quota to automatically generate quotas for subfolders on the volume or folder. [Create an Auto Apply Quota](create-auto-apply-quota)
5. Schedule a report task that contains a Quota Usage report to monitor quota usage periodically. [Schedule a Set of Reports](schedule-set-of-reports)

Note

If you want to screen files on a volume or folder, see [Checklist: Apply a File Screen to a Volume or Folder](checklist-apply-file-screen-to-volume-or-folder).