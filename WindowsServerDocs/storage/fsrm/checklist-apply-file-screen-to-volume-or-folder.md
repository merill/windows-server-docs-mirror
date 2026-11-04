---
layout: Conceptual
title: Checklist - Apply a file screen to a volume or folder | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/checklist-apply-file-screen-to-volume-or-folder
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to apply a file screen to a volume or folder
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: checklist
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: d364f9aa-69ce-33f1-9740-fd47678dbda2
document_version_independent_id: af4fd976-00ff-c490-a13a-ba6f33f4e26d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/checklist-apply-file-screen-to-volume-or-folder.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/checklist-apply-file-screen-to-volume-or-folder
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/checklist-apply-file-screen-to-volume-or-folder.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: eda6aa39-fdae-545b-3d2c-5d7a83c3efed
---

# Checklist - Apply a file screen to a volume or folder | Microsoft Learn

To apply a file screen to a volume or folder, use the following list:

1. Configure e-mail settings if you plan to send file screening notifications or storage reports by e-mail by following the instructions in [Configure E-Mail Notifications](configure-email-notifications).
2. Enable recording of file screening events in the auditing database if you plan to generate File Screening Audit reports. [Configure File Screen Audit](configure-file-screen-audit)
3. Assess stored file types that are candidates for screening rules. You can use reports at the **Storage Reports Management** node to provide data. (For example, run a Files by File Group report or a Large Files report on demand to identify files that occupy large amounts of disk space.) [Generate Reports on Demand](generate-reports-on-demand)
4. Review the preconfigured file groups, or create a new file group to enforce a specific screening policy in your organization. [Define File Groups for Screening](define-file-groups-for-screening)
5. Review the properties of available file screen templates. (In **File Screening Management**, click the **File Screen Templates** node.) [Edit File Screen Template Properties](edit-file-screen-template-properties) -Or-  Create a new file screen template to enforce a storage policy in your organization. [Create a File Screen Template](create-file-screen-template)
6. Create a file screen based on the template on a volume or folder. [Create a File Screen](create-file-screen)
7. Configure file screen exceptions in subfolders of the volume or folder. [Create a File Screen Exception](create-file-screen-exception)
8. Schedule a report task containing a File Screening Audit report to monitor screening activity periodically. [Schedule a Set of Reports](schedule-set-of-reports)

Note

To limit storage on a volume or folder, see [Checklist: Apply a Quota to a Volume or Folder](checklist-apply-file-screen-to-volume-or-folder)