---
layout: Conceptual
title: Create an Access Policy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/create-an-access-policy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to create an access policy in the IPAM client console.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 714ef634-e033-f3a7-7247-f7acdf7d86df
document_version_independent_id: a4dca32b-02bc-3e4f-dd0b-44f3aefe0cb1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Create-an-Access-Policy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/create-an-access-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Create-an-Access-Policy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 0cf3c3a8-bd3f-ba26-5e05-d554bc1259e2
---

# Create an Access Policy | Microsoft Learn

You can use this topic to create an access policy in the IPAM client console.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

Note

You can create an access policy for a specific user or for a user group in Active Directory. When you create an access policy, you must select either a built-in IPAM role or a custom role that you have created. For more information on custom roles, see [Create a User Role for Access Control](create-a-user-role-for-access-control).

### To create an access policy

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, click **ACCESS CONTROL**. In the lower navigation pane, right-click **Access Policies**, and then click **Add Access Policy**.

    ![Screenshot of Server Manager showing the Access Policies option highlighted and the Add Access Policy option available for selection.](../../media/create-an-access-policy/ipam_createap_01.jpg)
3. The **Add Access Policy** dialog box opens. In **User Settings**, click **Add**.

    ![Screenshot of the Add Access Policy dialog box.](../../media/create-an-access-policy/ipam_createap_02.jpg)
4. The **Select User or Group** dialog box opens. Click **Locations**.

    ![User or Group locations](../../media/create-an-access-policy/ipam_createap_03.jpg)
5. The **Locations** dialog box opens. Browse to the location that contains the user account, select the location, and then click **OK**. The **Locations** dialog box closes.

    ![Select location](../../media/create-an-access-policy/ipam_createap_04.jpg)
6. In the **Select User or Group** dialog box, in **Enter the object name to select**, type the user account name for which you want to create an access policy. Click **OK**.
7. In **Add Access Policy**, in **User Settings**, **User alias** now contains the user account to which the policy applies. In **Access Settings**, click **New**.

    ![New access setting](../../media/create-an-access-policy/ipam_createap_05.jpg)
8. In **Add Access Policy**, **Access Settings** changes to **New Setting**.

    ![Dialog box name change to New Setting](../../media/create-an-access-policy/ipam_createap_06.jpg)
9. Click **Select role** to expand the list of roles. Select one of the built-in roles or, if you have created new roles, select one of the roles that you created. For example, if you created the IPAMSrv role to apply to the user, click **IPAMSrv**.

    ![Select role](../../media/create-an-access-policy/ipam_createap_07.jpg)
10. Click **Add Setting**.

    ![Add new setting](../../media/create-an-access-policy/ipam_createap_08.jpg)
11. The role is added to the access policy. To create additional access policies, click **Apply**, and then repeat these steps for each policy that you want to create. If you do not want to create additional policies, click **OK**.

    ![Click Apply or OK](../../media/create-an-access-policy/ipam_createap_09.jpg)
12. In the IPAM client console display pane, verify that the new access policy is created.

    ![View the new access policy](../../media/create-an-access-policy/ipam_createap_09a.jpg)