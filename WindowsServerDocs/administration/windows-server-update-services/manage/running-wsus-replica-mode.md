---
layout: Conceptual
title: Running WSUS Replica mode | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-server-update-services/manage/running-wsus-replica-mode
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: wsus
ms.update-cycle: 1095-days
description: Windows Server Update Service (WSUS) topic - How to configure Replica mode
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e7390f85-8172-7776-c538-886611db1860
document_version_independent_id: 8478b2f0-7117-faf2-896e-ba97f1a0a246
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-server-update-services/manage/running-wsus-replica-mode.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-server-update-services/manage/running-wsus-replica-mode
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-server-update-services/manage/running-wsus-replica-mode.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b3a1d390-85fd-16ae-cd57-9cefa6b45853
---

# Running WSUS Replica mode | Microsoft Learn

A WSUS server running in replica mode inherits the update approvals and computer groups created on an administration server. In a scenario that uses replica mode, you typically have a single administration server, and one or more subordinate replica WSUS servers spread out throughout the organization, based on site or organizational topography. You approve updates and create computer groups on the administration server, which the replica mode servers will then mirror. Replica mode servers can be set up only during WSUS Setup, and if you implemented this scenario, it is likely because it is important in your organization that update approvals and computer groups are managed centrally.

If your WSUS server is running in replica mode, you will be able to perform only limited administration capabilities on the server, which will primarily consist of:

- Adding and removing computers from computer groups. Computer group membership is not distributed to replica servers, only the computer groups themselves. Therefore, on a replica mode server, you will inherit the computer groups that you created on the administration server. However, the computer groups will be empty. You must then assign the client computers that connect to the replica server to the computer groups.
- Setting a synchronization schedule
- Specifying proxy-server settings
- Specifying the update source. This can be a server other than the administration server
- Viewing available updates
- Monitoring update, synchronization, computer status, and WSUS settings on the server
- Running all standard WSUS reports available on replica mode servers