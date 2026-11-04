---
layout: Conceptual
title: Purge Utilization Data | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/purge-utilization-data
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to delete utilization data from the IPAM database.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 3ff9faf1-0f33-01f2-3406-aa2e0417c591
document_version_independent_id: 20529fb2-96f0-5e89-79c8-f28f8be88b52
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Purge-Utilization-Data.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/purge-utilization-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Purge-Utilization-Data.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 9d2aee62-8e92-cca5-42b8-c8aa5520dca4
---

# Purge Utilization Data | Microsoft Learn

You can use this topic to learn how to delete utilization data from the IPAM database.

You must be a member of **IPAM Administrators**, the local computer **Administrators** group, or equivalent, to perform this procedure.

## To purge the IPAM database

1. Open Server Manager, and then browse to the IPAM client interface.
2. Browse to one of the following locations: **IP Address Blocks**, **IP Address Inventory**, or **IP Address Range Groups**.
3. Click **TASKS**, and then click **Purge Utilization Data**. The **Purge Utilization Data** dialog box opens.
4. In **Purge all utilization data on or before**, click **Select a date**.
5. Choose the date for which you want to delete all database records both on and before that date.
6. Click **OK**. IPAM deletes all the records that you have specified.