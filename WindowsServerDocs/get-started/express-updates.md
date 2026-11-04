---
layout: Conceptual
title: Express updates for Windows Server 2016 re-enabled for November 2018 update | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/express-updates
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Provides information about Express Updates in Windows Server 2016
ms.topic: release-notes
author: robinharwood
ms.author: roharwoo
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: e6babdbf-18d1-937a-202f-4ab8fd030771
document_version_independent_id: 32058fe0-4e4b-db9f-5824-c9443922b417
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/express-updates.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/express-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/express-updates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 6d98cea5-4861-14a8-0998-b8c12b6586d8
---

# Express updates for Windows Server 2016 re-enabled for November 2018 update | Microsoft Learn

> 
> Applies to: Windows Server 2016

Starting with the November 13, 2018 Update Tuesday, Windows will again publish Express updates for Windows Server 2016. Express updates for Windows Server 2016 stopped in mid-2017 after a significant issue was found that kept the updates from installing correctly. While the issue was fixed in November 2017, the update team took a conservative approach to publishing the Express packages to ensure most customers would have the November 14, 2017 update ([KB 4048953](https://support.microsoft.com/help/4048953/windows-10-update-kb4048953)) installed on their server environments and not be impacted by the issue.

System administrators for WSUS and Configuration Manager need to be aware that in November 2018 they will once again see two packages for the Windows Server 2016 update: a Full update and an Express update. System administrators who want to use Express for their server environments need to confirm that the device has taken a full update since November 14, 2017 ([KB 4048953](https://support.microsoft.com/help/4048953/windows-10-update-kb4048953)) to ensure the Express update installs correctly. Any device which has not been updated since the November 14, 2017 update ([KB 4048953](https://support.microsoft.com/help/4048953/windows-10-update-kb4048953)) will see repeated failures that consume bandwidth and CPU resources in an infinite loop if the Express update is attempted. Remediation for that state would be for the system administrator to stop pushing the Express update and push a recent Full update to stop the failure loop.

With the November 13, 2018 Express update customers will see an immediate reduction of package size between their management system and the Windows Server 2016 end points.