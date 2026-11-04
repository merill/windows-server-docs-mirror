---
layout: Conceptual
title: Create and Manage Server Groups | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/server-manager/create-and-manage-server-groups
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Learn how to create custom, user-defined groups of servers in Server Manager in Windows Server.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a469e427-b56a-501e-be09-4c22e4d0c0d0
document_version_independent_id: c859985f-32f6-dddf-57eb-a344a992f7ae
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/server-manager/create-and-manage-server-groups.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/server-manager/create-and-manage-server-groups
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/server-manager/create-and-manage-server-groups.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 5884b4e4-65cb-9a3e-f9a5-1c3ce975fdfb
---

# Create and Manage Server Groups | Microsoft Learn

This topic describes how to create custom, user-defined groups of servers in Server Manager in Windows Server.

## Server groups

Servers that you add to the server pool are displayed on the **All Servers** page in Server Manager. You can create custom groups of servers that you have added. Server groups allow you to view and manage a smaller subset of your server pool as a logical unit; for example, you can create a group called **Accounting Servers** for all servers in your organization's Accounting department, or a group called **Chicago** for all servers that are geographically located in Chicago. After you create a server group, the group's home page in Server Manager displays information about events, services, performance counters, Best Practices Analyzer results, and installed roles and features for the group as a whole.

Servers can be a member of more than one group.

#### To create a new server group

1. On the **Manage** menu, click **create Server Group**.
2. In the **Server group name** text box, type a friendly name for your server group, such as **Accounting Servers**.
3. add servers to the **selected** list from the server pool, or add other servers to the group by using the **active directory**, **DNS**, or **import** tabs. For more information about how to use these tabs, see [add Servers to Server Manager](add-servers-to-server-manager) in this guide.
4. When you have finished adding servers to the group, click **OK**. The new group is displayed in the Server Manager navigation pane under the **All Servers** group.

#### To edit an existing server group

1. Do one of the following.

    - In the Server Manager navigation pane, right-click a server group, and then click **edit Server Group**.
    - On the home page for the server group, open the **Tasks** menu on the **Servers** tile, and then click **edit Server Group**.
2. change the group name, or add or remove servers from the group.

    Note

    removing servers from a server group does not remove servers from Server Manager. Servers that you remove from a group remain in the **All Servers** group, in the server pool.
3. When you are finished with changes to the group, click **OK**.

#### To delete an existing server group

1. Do one of the following.

    - In the Server Manager navigation pane, right-click a server group, and then click **delete Server Group**.
    - On the home page for the server group, open the **Tasks** menu on the **Servers** tile, and then click **delete Server Group**.
2. When you are prompted to make sure you want to delete the server group, click **Yes**.

    Note

    deleting a server group does not remove servers from Server Manager. Servers that were in a deleted group remain in the **All Servers** group, in the server pool.
3. When you are finished with changes to the group, click **OK**.