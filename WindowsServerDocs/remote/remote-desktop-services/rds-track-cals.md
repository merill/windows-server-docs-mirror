---
layout: Conceptual
title: Track your Remote Desktop Services client access licenses (RDS CALs) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-track-cals
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to track CALs across your RDS deployment.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: 5db2bb5f-5b0a-fe7f-acf8-5760dd0df259
document_version_independent_id: 8a3ba9d8-2696-7652-0c9c-90b3bb70d9dc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-track-cals.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-track-cals
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-track-cals.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: c7067fc4-8a51-03d8-b3dc-da2a1ff92d85
---

# Track your Remote Desktop Services client access licenses (RDS CALs) | Microsoft Learn

You can use the Remote Desktop Licensing Manager tool to create reports to track the RDS Per User CALs that have been issued by a Remote Desktop license server.

Note

If you're using Microsoft Entra Domain Services in your environment, the Remote Desktop Licensing Manager tool won't work to obtain Per User CALs. Instead, you need to track licensing manually, either through logon events, polling active Remote Desktop connections through the Connection Broker, or another mechanism that works for you.

Use the following steps to generate a per User CALs report:

1. In Remote Desktop Licensing Manager right-click the license server, click **Create Report**, and then click **CAL Usage**.
2. The report is created and a message appears to confirm that the report was successfully created. Click **OK** to close the message.

The report that you created appears in the Reports section under the node for the license server. The report provides the following information:

- Date and time the report was created
- The scope of the report (e.g., Domain, OU=Sales, or All trusted domains)
- The number of RDS Per User CALs that are installed on the license server
- The number of RDS Per User CALs that have been issued by the license server specific to the scope of the report

You can also save the report as a CSV file to a folder location on the computer. To save the report, right-click the report that you want to save, click Save As, and then specify the file name and location to save the report.

Reports that you create are listed in the Reports node under the node for the license server in Remote Desktop Licensing Manager. If you no longer need a report, you can delete it.