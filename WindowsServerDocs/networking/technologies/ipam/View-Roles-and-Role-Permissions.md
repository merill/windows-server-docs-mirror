---
layout: Conceptual
title: View Roles and Role Permissions | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/view-roles-and-role-permissions
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to view Access Control user roles in the IPAM client console.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 4c9d275f-1d30-c364-ecc2-a29c369ac094
document_version_independent_id: e714cc54-f979-1488-519e-0347441cb3b2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/View-Roles-and-Role-Permissions.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/view-roles-and-role-permissions
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/View-Roles-and-Role-Permissions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d6ae8417-1f11-82fe-452c-ecd2116334d7
---

# View Roles and Role Permissions | Microsoft Learn

You can use this topic to view Access Control user roles in the IPAM client console.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

### To view Access Control roles

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, click **ACCESS CONTROL**.
3. In the lower navigation pane, click **Roles**. In the display pane, the roles are listed.

    ![In the display pane the roles are listed](../../media/view-roles-and-role-permissions/ipam_viewroles_01.jpg)
4. Select the role whose permissions you want to view. In the lower details pane, the operations that are permitted for the role are displayed.

    ![View role permissions](../../media/view-roles-and-role-permissions/ipam_viewroles_02.jpg)