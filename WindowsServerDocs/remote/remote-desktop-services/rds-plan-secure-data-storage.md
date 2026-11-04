---
layout: Conceptual
title: Remote Desktop Services - Secure data storage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-plan-secure-data-storage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Planning information for securely storing data by using user profile disks (UPDs) in RDS.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: f373cf3c-1643-2eb9-1b4a-7ce6b379c6ba
document_version_independent_id: ebd5b4a4-ffe0-0473-a51f-0a55a447493c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-plan-secure-data-storage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-plan-secure-data-storage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-plan-secure-data-storage.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: aaebf174-dbcf-eb8a-87c9-fb794c42644e
---

# Remote Desktop Services - Secure data storage | Microsoft Learn

Store business resources, user personalization data, and settings securely on-premises or in Azure. RD Session Hosts use AD authentication and empower users with the resources they need in a personalized environment, securely.

Ensuring users have a consistent experience, regardless of the endpoint from which they access their remote resources, is an important aspect of managing an RDS deployment. User Profile Disks (UPDs) allow user data, customizations, and application settings to follow a user within a single collection. A UPD is a per-user, per-collection VHD file saved in a central share that is mounted to a user's session when they sign in - the UPD is treated as a local drive for the duration of that session.

From the user's perspective, the UPD provides a famililar experience - they save their documents to their Documents folder (on what appears to be a local drive), change their app settings as usual, and make any customizations to their Windows environment. All this data, including the registry hive, is stored on the UPD and persists in a central network share. UPDs are only available to the user when the user is actively connected to a desktop or RemoteApp. UPDs can only roam within a collection because the user's entire `C:\Users\<username\>` directory (including AppData\Local) is stored on the UPD.

You can use [PowerShell cmdlets](/en-us/powershell/module/remotedesktop/set-rdsessioncollectionconfiguration) to designate the path to the central share, the size of each UPD, and which folders should be included or excluded from the user profile saved to the UPD. Alternatively, you can enable UPDs through Server Manager by going to **Remote Desktop Services** &gt; **Collections** &gt; **Desktop Collection** &gt; **Desktop Collection Properties** &gt; **User Profile Disks**. Note that you enable or disable UPDs for all users of an entire collection, not for specific users in that collection. UPDs must be stored on a central file share where the servers in the collection have full control permissions.

You can achieve high availability for your UPDs by storing them in Azure with [Storage Spaces Direct](rds-storage-spaces-direct-deployment).