---
layout: Conceptual
title: Create a User Role for Access Control | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/create-a-user-role-for-access-control
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to create a new Access Control user role in the IPAM client console.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: f5c54bf2-2ff6-acd0-1953-a59def2ce340
document_version_independent_id: d7f4ef9f-982a-4d15-97eb-9a3b2c584885
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Create-a-User-Role-for-Access-Control.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/create-a-user-role-for-access-control
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Create-a-User-Role-for-Access-Control.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: e5868638-bded-6136-4127-e8d3e692e688
---

# Create a User Role for Access Control | Microsoft Learn

You can use this topic to create a new Access Control user role in the IPAM client console.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

Note

After you create a role, you can create an access policy to assign the role to a specific user or Active Directory group. For more information, see [Create an Access Policy](create-an-access-policy).

### To create a role

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, click **ACCESS CONTROL**, and in the lower navigation pane, click **Roles**.

    ![Access control roles](../../media/create-a-user-role-for-access-control/ipam_createuserrole_01.jpg)
3. Right-click **Roles**, and then click **Add User Role**.

    ![Add User Role](../../media/create-a-user-role-for-access-control/ipam_createuserrole_02.jpg)
4. The **Add or Edit Role** dialog box opens. In **Name**, type a name for the role that makes the role function clear. For example, if you want to create a role that allows Administrators to manage DNS SRV resource records, you might name the role **IPAMSrv**. If needed, scroll down in **Operations** to locate the type of operations you want to define for the role. For this example, scroll down to **DNS resource record management operations**.

    ![DNS resource record management operations](../../media/create-a-user-role-for-access-control/ipam_createuserrole_03.jpg)
5. Expand **DNS resource record management operations**, and then locate **SRV record operations**.

    ![SRV record operations](../../media/create-a-user-role-for-access-control/ipam_createuserrole_04.jpg)
6. Expand and select **SRV record operations**, and then click **OK**.

    ![Select SRV record operations](../../media/create-a-user-role-for-access-control/ipam_createuserrole_05.jpg)
7. In the IPAM client console, click the role that you just created. In **Details View,** the permitted operations for the role are displayed.

    ![New role details](../../media/create-a-user-role-for-access-control/ipam_createuserrole_06.jpg)