---
layout: Conceptual
title: Server Cleanup wizard | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-server-update-services/manage/the-server-cleanup-wizard
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: wsus
ms.update-cycle: 1095-days
description: Windows Server Update Service (WSUS) article - How to use the Server Cleanup wizard to manage disk space.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2023-05-10T00:00:00.0000000Z
locale: en-us
document_id: 2e9e9c15-b10c-4a86-e02f-2292f3755f48
document_version_independent_id: f343b9a3-b7ef-dd1c-158b-a2a112b16fd2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-server-update-services/manage/the-server-cleanup-wizard.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-server-update-services/manage/the-server-cleanup-wizard
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-server-update-services/manage/the-server-cleanup-wizard.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 9990c34c-20f6-9149-46f1-114d7920be6b
---

# Server Cleanup wizard | Microsoft Learn

Applies to: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

The Server Cleanup wizard is integrated into the user interface to help you manage your disk space. The Server Cleanup wizard can do the following operations:

- Remove unused updates and update revisions.
- Remove all older updates and update revisions that haven't been approved.
- Delete all client computers that haven't contacted the server in 30 days or longer.
- Delete all update files that aren't needed by updates or by downstream servers.
- Decline all updates that are expired by Microsoft.
- Decline all updates that meet all the following criteria:

    - The superseded update isn't mandatory.
    - The superseded update has been on the server for 30 days or more.
    - The superseded update isn't currently reported as needed by any client.
    - The superseded update hasn't been explicitly deployed to a computer group for 90 days or longer.
    - The superseding update must be approved for install to a computer group.

    Warning

    In a WSUS hierarchy, it's strongly recommended that you run the cleanup process on the lower-most, downstream/replica WSUS server first and then move up the hierarchy. Incorrectly running cleanup on any upstream server prior to running cleanup on every downstream server can cause a mismatch between the data that's present in upstream databases and downstream databases. The data mismatch can lead to synchronization failures between the upstream and downstream servers.

    Important

    If you remove unnecessary content using the Server Cleanup wizard, all the private update files that you've downloaded from the Microsoft Update Catalog site are also removed. You must reimport these files after you run the Server Cleanup wizard.

If updates are approved using an autoapproval rule, they could remain in an Approved state and won't be removed by The Server Cleanup wizard. To remove autoapproved updates that are in an Approved state, the WSUS Admin must at minimum manually set the approval status of superseded updates to Not Approved. Manually setting approval status of superseded updates to Not Approved make the updates eligible for declination by the Server Cleanup wizard. The Server Cleanup wizard ensures a newer update is approved and that no client system is still reporting these updates as needed before marking the update as Declined.