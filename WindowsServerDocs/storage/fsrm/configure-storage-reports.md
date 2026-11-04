---
layout: Conceptual
title: Configure Storage Reports | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/configure-storage-reports
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to configure the default parameters for storage reports
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 709901a2-208c-9f38-1b21-42f9f0a4e6e9
document_version_independent_id: 4b059778-3cf1-09d9-bcfb-1acca5ca464d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/configure-storage-reports.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/configure-storage-reports
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/configure-storage-reports.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
platformId: a9a004e5-8372-732c-90b5-82ffbbb371a6
---

# Configure Storage Reports | Microsoft Learn

You can configure the default parameters for storage reports. These default parameters are used for the incident reports that are generated when a quota or file screening event occurs. They are also used for scheduled and on-demand reports, and you can override the default parameters when you define the specific properties of these reports.

Important

When you change the default parameters for a type of report, changes affect all incident reports and any existing scheduled report tasks that use the defaults.

## To configure the default parameters for Storage Reports

1. In the console tree, right-click **File Server Resource Manager**, and then click **Configure Options**. The **File Server Resource Manager Options** dialog box opens.
2. On the **Storage Reports** tab, under **Configure default parameters**, select the type of report that you want to modify.
3. Click **Edit Parameters**.
4. Depending on the type of report that you select, different report parameters will be available for editing. Perform all necessary modifications, and then click **OK** to save them as the default parameters for that type of report.
5. Repeat steps 2 through 4 for each type of report that you want to edit.
6. To see a list of the default parameters for all reports, click **Review Reports**. Then click **Close**.
7. Click **OK**.

## Additional References

- [Setting File Server Resource Manager Options](setting-file-server-resource-manager-options)
- [Storage Reports Management](storage-reports-management)