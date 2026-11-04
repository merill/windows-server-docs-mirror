---
layout: Conceptual
title: Network Policy Server user data collection | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-data-collection
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: What information is used to help authenticate users by Network Policy Server in Windows Server 2016.
author: robinharwood
ms.author: roharwoo
ms.reviewer: 
ms.custom: it-pro
ms.topic: concept-article
ms.date: 2024-05-29T00:00:00.0000000Z
locale: en-us
document_id: d6b87f2d-605f-e821-3700-83f57af86e9d
document_version_independent_id: 59b1ca3e-21f8-f342-ac9b-3e42df6cdd13
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-data-collection.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-data-collection
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-data-collection.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: ef26598a-9a6a-a677-0ecc-790d015fbb69
---

# Network Policy Server user data collection | Microsoft Learn

This document explains how to find user information collected by the Network Policy Server (NPS) in the event you would like to remove it.

Note

If you're interested in viewing or deleting personal data, please review Microsoft's guidance in the [Windows Data Subject Requests for the GDPR](/en-us/microsoft-365/compliance/gdpr-dsr-windows) site. If you're looking for general information about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## Information Collected by NPS

- Timestamp
- Event Timestamp
- Username
- Full Qualified Username
- Client IP Address
- Client Vendor
- Client Friendly Name
- Authentication Type
- Numerous other fields concerning the RADIUS protocol

## Gather data from NPS

If accounting data is enabled and configured, then records of a user's NPS authentication attempts can be obtained from SQL Server or the log files depending on the configuration.

If accounting data is configured for SQL Server, query for all records WHERE User\_Name = `'<username>'`.

If accounting data is configured for a log file, then search the log file for the `<username>` to find all log entries.

Network Policy and Access Services event log entries are considered duplicative to the accounting data and don't need to be collected.

If accounting data is not enabled, then records of a user's NPS authentication attempts can be obtained from the Network Policy and Access Services event log by searching for the `<username>`.