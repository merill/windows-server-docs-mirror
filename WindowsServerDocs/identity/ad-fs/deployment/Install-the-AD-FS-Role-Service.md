---
layout: Conceptual
title: Install the AD FS Role Service | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/install-the-ad-fs-role-service
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Install the AD FS Role Service'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: install-set-up-deploy
locale: en-us
document_id: a6363849-a4ec-cb51-a943-a9dcb49657e0
document_version_independent_id: 378105e4-a7d3-5e52-5815-18035b849383
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Install-the-AD-FS-Role-Service.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/install-the-ad-fs-role-service
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Install-the-AD-FS-Role-Service.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/e2d3fbf8-36df-4730-9ac5-e1c53887f039
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 07975752-043c-dd70-10e8-6367222b4854
---

# Install the AD FS Role Service | Microsoft Learn

You can use the following procedure to install the AD FS role service on a computer that is running Windows Server 2012 R2 to become the first federation server in a federation server farm or a federation server in an existing federation server farm.

Membership in **Administrators**, or equivalent, on the local computer is the minimum requirement to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

### To install the AD FS server role via the Add roles and features wizard

1. Open Server Manager. To open Server Manager, click **Server Manager** on the **Start** screen, or **Server Manager** in the taskbar on the desktop. In the **Quick Start** tab of the **Welcome** tile on the **Dashboard** page, click **Add roles and features**. Alternatively, you can click **Add Roles and Features** on the **Manage** menu.
2. On the **Before you begin** page, click **Next**.
3. On the **Select installation type** page, click **Role-based or Feature-based installation**, and then click **Next**.
4. On the **Select destination server** page, click **Select a server from the server pool**, verify that the target computer is selected, and then click **Next**.
5. On the **Select server roles** page, click **Active Directory Federation Services**, and then click **Next**.
6. On the **Select features** page, click **Next**. The required prerequisites are preselected for you. You do not have to select any other features.
7. On the **Active Directory Federation Service (AD FS)** page, click **Next**.
8. After you verify the information on the **Confirm installation selections** page, click **Install**.
9. On the **Installation progress** page, verify that everything installed correctly, and then click **Close**.

### To install the AD FS server role via Windows PowerShell

1. On the computer that you want to configure as a federation server, open the Windows PowerShell command window, and then run the following command: `Install-windowsfeature adfs-federation -IncludeManagementTools`.