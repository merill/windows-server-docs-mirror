---
layout: Conceptual
title: Manage users in your RDS collection | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-user-management
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to manage users in Remote Desktop Services.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: fc6eb8ed-549f-7280-8d99-b5f1cf2e29d5
document_version_independent_id: 65c88dec-88dc-8e60-014e-78f5cf21407f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-user-management.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-user-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-user-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 8d1bf2be-5aaf-653b-8877-91167a47f176
---

# Manage users in your RDS collection | Microsoft Learn

As an admin, you can directly manage which users have access to specific collections. This way, you can create one collection with standard applications for information workers, but then create a separate collection with graphics-intensive modeling applications for engineers. There are two primary steps to managing user access in a Remote Desktop Services (RDS) deployment:

1. Create users and groups in Active Directory
2. Assign users and groups to collections

## Create your users and groups in Active Directory

In an RDS deployment, Active Directory Domain Services (AD DS) is the source of all users, groups, and other objects in the domain. You can manage Active Directory directly with PowerShell, or you can use built in UI tools that add ease and flexibility. The following steps will guide you to install those tools — if you do not have them already installed — and then use those tools to manage users and groups.

### Install AD DS tools

The following steps detail how to install the AD DS tools on a server already running AD DS. Once installed, you can then create users or create groups.

1. Connect to the server running Active Directory Domain Services. For Azure deployments:
    1. In the Azure portal, click **Browse &gt; Resource groups**, and then click the resource group for the deployment
    2. Select the AD virtual machine.
    3. Click **Connect &gt; Open** to open the Remote Desktop client. If **Connect**is grayed out, the virtual machine might not have a public IP address. To give it one perform the following steps, then try this step again.
        1. Click **Settings &gt; Network interfaces**, and then click the corresponding network interface.
        2. Click **Settings &gt; IP address**.
        3. For **Public IP address**, select **Enabled**, and then click **IP address**.
        4. If you have an existing public IP address you want to use, select it from the list. Otherwise, click **Create new**, enter a name, and then click **OK** and **Save**.
    4. In the client, click **Connect**, and then click **Use another account**. Enter the user name and password for a domain administrator account.
    5. Click **Yes** when asked about the certificate.
2. Install the AD DS tools:
    1. In Server Manager click **Manage &gt; Add Roles and Features**.
    2. Click **Role-based or feature-based installation**, and then click the current AD server. Follow the steps until you get to the **Features** tab.
    3. Expand **Remote Server Administration Tools &gt; Role Administration Tools &gt; AD DS and AD LDS Tools**, and then select **AD DS Tools**.
    4. Select **Restart the destination server automatically if required**, and then click **Install**.

### Create a group

You can use AD DS groups to grant access to a set of users that need to use the same remote resources.

1. In Server Manager on the server running AD DS, click **Tools &gt; Active Directory Users and Computers**.
2. Expand the domain in the left-hand pane to view its subfolders.
3. Right-click the folder where you want to create the group, and then click **New &gt; Group**.
4. Enter an appropriate group name, then select **Global** and **Security**.

### Create a user and add to a group

1. In Server Manager on the server running AD DS, click **Tools &gt; Active Directory Users and Computers**.
2. Expand the domain in the left-hand pane to view its subfolders.
3. Right-click **Users**, and then click **New &gt; User**.
4. Enter, at minimum, a first name and a user logon name.
5. Enter and confirm a password for the user. Set appropriate user options, like **User must change password at next logon**.
6. Add the new user to a group:
    1. In the **Users** folder right-click the new user.
    2. Click **Add to a group**.
    3. Enter the name of the group to which you want to add the user.

## Assign users and groups to collections

Now that you've created the users and groups in Active Directory, you can add some granularity regarding who has access to the Remote Desktop collections in your deployment.

1. Connect to the server running the Remote Desktop Connection Broker (RD Connection Broker) role, following the steps described earlier.
2. Add the other Remote Desktop servers to the RD Connection Broker's pool of managed servers:

    1. In Server Manager click **Manage &gt; Add Servers**.
    2. Click **Find Now**.
    3. Click each server in your deployment that is running a Remote Desktop Services role, and then click **OK**.
3. Edit a collection to assign access to specific users or groups:

    1. In Server Manager click **Remote Desktop Services &gt; Overview**, and then click a specific collection.
    2. Under **Properties**, click **Tasks &gt; Edit properties**.
    3. Click **User groups**.
    4. Click **Add** and enter the user or group that you want to have access to the collection. You can also remove users and groups from this window by selecting the user or group you want to remove, and then clicking **Remove**.

    Note

    The User groups window can never be empty. To narrow the scope of users who have access to the collection, you must first add specific users or groups before removing broader groups.