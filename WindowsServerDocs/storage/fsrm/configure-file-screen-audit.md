---
layout: Conceptual
title: Configure File Screen Audit | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/configure-file-screen-audit
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to configure File Screen Audit to generate the File Screening Audit report
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 24818f7c-21ef-94f2-6060-d3e0004fbd9c
document_version_independent_id: 32973ef7-faa4-d586-c1de-3d2f7a1ef605
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/configure-file-screen-audit.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/configure-file-screen-audit
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/configure-file-screen-audit.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d9c69970-76c4-3b7b-2742-eccd5ca35c9d
---

# Configure File Screen Audit | Microsoft Learn

By using File Server Resource Manager, you can record file screening activity in an auditing database. The information saved in this database is used to generate the File Screening Audit report.

Important

If the **Record file screening activity in the auditing database** check box is cleared, the File Screening Audit Reports will not contain any information.

## To configure file screen audit

1. In the console tree, right-click **File Server Resource Manager**, and then click **Configure Options**. The **File Server Resource Manager Options** dialog box opens.
2. On the **File Screen Audit** tab, select the **Record file screening activity in the auditing database** check box.
3. Click **OK**. All file screening activity will now be stored in the auditing database, and it can be viewed by running a File Screening Audit report.

## Additional References

- [Setting File Server Resource Manager Options](setting-file-server-resource-manager-options)
- [Storage Reports Management](storage-reports-management)