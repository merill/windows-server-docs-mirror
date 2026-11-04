---
layout: Conceptual
title: Prepare Your Environment for Windows Admin Center | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/deploy/prepare-environment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Prepare your environment for Windows Admin Center (Project Honolulu).
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2019-06-07T00:00:00.0000000Z
locale: en-us
document_id: a65d64c7-5f3f-e516-c9c9-0f0cebe100fe
document_version_independent_id: 0bff8d8c-c692-b862-a906-483d7430415d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/deploy/prepare-environment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/deploy/prepare-environment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/deploy/prepare-environment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 308d35cc-ee40-05ce-7ae5-a42fcc06d75b
---

# Prepare Your Environment for Windows Admin Center | Microsoft Learn

Some server versions need more preparation before they're ready for you to manage by using Windows Admin Center:

- Windows Server 2012 and 2012 R2
- Microsoft Hyper-V Server 2016
- Microsoft Hyper-V Server 2012 R2

You might also need to modify port configuration on the target server before you can manage it by using Windows Admin Center.

## Prepare Windows Server 2012 and 2012 R2

### Install Windows Management Framework version 5.1 or higher

Windows Admin Center requires Windows PowerShell features that aren't included by default in Windows Server 2012 and 2012 R2. To manage Windows Server 2012 or 2012 R2 by using Windows Admin Center, you need to install Windows Management Framework version 5.1 or higher on those servers.

Enter `$PSVersiontable` in PowerShell to verify that Windows Management Framework is installed and that the version is 5.1 or higher. If it isn't installed, [download and install Windows Management Framework 5.1](/en-us/powershell/scripting/wmf/setup/install-configure).

## Prepare Microsoft Hyper-V Server 2016

To manage Microsoft Hyper-V Server 2016 by using Windows Admin Center, you need to enable some server roles.

### Manage Microsoft Hyper-V Server 2016 by using Windows Admin Center

1. Enable remote management.
2. Enable the File Server role.
3. Enable the Hyper-V module for PowerShell.

### Step 1: Enable remote management

To enable remote management in Hyper-V Server:

1. Sign in to Hyper-V Server.
2. At the **Server Configuration** (`SCONFIG`) tool, enter **4** to configure remote management.
3. Enter **1** to enable remote management.
4. Enter **4** to return to the main menu.

### Step 2: Enable the File Server role

To enable the File Server role for basic file sharing and remote management:

1. On the **Tools** menu, select **Roles & features**.
2. In the **Roles and features** pane, find **File and Storage Services**, and select **File and iSCSI Services** &gt; **File Server**.

    ![Screenshot that shows the Roles and features pane with the File Server role selected.](../media/prepare-environment/prepare-your-environment-image-1.png)

### Step 3: Enable Hyper-V module for PowerShell

To enable Hyper-V module for PowerShell features:

1. On the **Tools** menu, select **Roles & features**.
2. In the **Roles and features** pane, find **Remote Server Administration Tools** and select **Role Administration Tools** &gt; **Hyper-V Module for Windows PowerShell**.

    ![Screenshot that shows Roles and features with Hyper-V roles selected.](../media/prepare-environment/prepare-your-environment-image-2.png)

Microsoft Hyper-V Server 2016 is now ready for management by using Windows Admin Center.

## Prepare Microsoft Hyper-V Server 2012 R2

To manage Microsoft Hyper-V Server 2012 R2 by using Windows Admin Center, you need to enable some server roles. You also need to install Windows Management Framework version 5.1 or higher.

### Manage Microsoft Hyper-V Server 2012 R2 by using Windows Admin Center

1. Install Windows Management Framework version 5.1 or higher.
2. Enable remote management.
3. Enable the File Server role.
4. Enable the Hyper-V module for PowerShell.

### Step 1: Install Windows Management Framework 5.1

Windows Admin Center requires PowerShell features that aren't included by default in Microsoft Hyper-V Server 2012 R2. To manage Microsoft Hyper-V Server 2012 R2 by using Windows Admin Center, you need to install Windows Management Framework version 5.1 or higher.

Enter `$PSVersiontable` in PowerShell to verify that Windows Management Framework is installed and that the version is 5.1 or higher.

If it isn't installed, you can [download Windows Management Framework 5.1](/en-us/powershell/scripting/wmf/setup/install-configure).

### Step 2: Enable remote management

To enable Hyper-V Server remote management:

1. Sign in to Hyper-V Server.
2. At the **Server Configuration** (`SCONFIG`) tool, enter **4** to configure remote management.
3. Enter **1** to enable remote management.
4. Enter **4** to return to the main menu.

### Step 3: Enable the File Server role

To enable the File Server role for basic file sharing and remote management:

1. On the **Tools** menu, select **Roles & features**.
2. In the **Roles and features** pane, find **File and Storage Services** and select **File and iSCSI Services** &gt; **File Server**.

    ![Screenshot that shows the Roles and features pane with the File Server role selected.](../media/prepare-environment/prepare-your-environment-image-1.png)

### Step 4: Enable the Hyper-V module for PowerShell

To enable the Hyper-V module for PowerShell features:

1. On the **Tools** menu, select **Roles & features**.
2. In the **Roles and features** pane, find **Remote Server Administration Tools** and select **Role Administration Tools** &gt; **Hyper-V Module for Windows PowerShell**.

    ![Screenshot that shows the Roles and features pane with Hyper-V Module for Windows PowerShell selected.](../media/prepare-environment/prepare-your-environment-image-2.png)

Microsoft Hyper-V Server 2012 R2 is now ready for management by using Windows Admin Center.

## Port configuration on the target server

Windows Admin Center uses the Server Message Block (SMB) file-sharing protocol for some file-copying tasks, such as importing a certificate on a remote server. For these file copy operations to succeed, the firewall on the remote server must allow inbound connections on port 445. You can use the Firewall tool in Windows Admin Center to verify that the incoming rule for `File Server Remote Management (SMB-In)` is set to allow access on this port.

Tip

Ready to install Windows Admin Center? [Download now](../overview#download-now).