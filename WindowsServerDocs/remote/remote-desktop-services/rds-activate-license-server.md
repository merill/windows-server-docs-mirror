---
layout: Conceptual
title: Activate the Remote Desktop Services license server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-activate-license-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Install and activate the RD license server
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2025-02-14T00:00:00.0000000Z
locale: en-us
document_id: 2499f6d6-b28d-d46b-ea9d-3c9dd54fee7c
document_version_independent_id: cd210491-0f3a-1b60-c739-f74bd58daae4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-activate-license-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-activate-license-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-activate-license-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: e4e76171-e236-b586-6979-9d6c1754a251
---

# Activate the Remote Desktop Services license server | Microsoft Learn

The Remote Desktop Services license server issues client access licenses (CALs) to users and devices when they access the RD Session Host. You can activate the license server by using the Remote Desktop Licensing Manager.

## Prerequisites

Before you can activate your Remote Desktop Services license server, ensure that you have:

- A Windows Server with the Remote Desktop Services licensing role service installed, including the Remote Desktop Licensing Tools feature.
- Administrative privileges on the server.
- A basic understanding of Remote Desktop licensing.
- You need to have you company information ready to enter during the activation process.

## Install the Remote Desktop Licensing role

1. Sign into the server you want to use as the license server using an administrator account.
2. In Server Manager, select **Manage** &gt; **Add Roles and Features**.
3. On the **Select installation type** page, select **Role-based or feature-based installation**.
4. Specify the server on which you install the licensing role.
5. On the **Server Roles** page, check the box for **Remote Desktop Services**, then select **Next** until you see the **Remote Desktop Services** page.
6. Select the roles you want to install. Make sure you include the **Remote Desktop Licensing** role.
7. In the **Add Roles and Features Wizard** dialog box, select **Add Features**.
8. Select **Next** until you see the **Confirmation** page, then select **Install**.

For detailed information and other installation options, see [Install or uninstall roles, role services, or features](../../administration/server-manager/install-or-uninstall-roles-role-services-or-features)

## Activate the license server

1. In Server Manager, select **Tools** &gt; **Remote Desktop Services** &gt; **Remote Desktop Licensing Manager**.
2. In the **RD Licensing Manager**, select the server, and then select **Action** &gt; **Activate Server**.
3. Confirm your preferred Connection method for license server activation and select **Next**. The three options available are:

    - **Automatic connection (recommended)**: This recommended method communicates via internet directly to the Microsoft Clearinghouse outbound over TCP port 443.
    - **Web Browser**: This method requires the administrator to connect to the Microsoft Clearinghouse web site. Use this method if the license server doesn't have internet access, but you have internet access through another computer.
    - **Telephone**: This method allows the administrator to complete the migration process over the phone with a Microsoft Clearinghouse operator. Use this method if you don't have internet access.

### Activate with automatic connection

1. Enter your required **Company information** including First name, Family name, Company, and Country or Region. Select **Next**.
2. Then enter your optional company information. Select **Next** until you complete the Activate Server Wizard.
3. Accept the defaults for the remaining pages until the final page. Clear **Start Install Licenses Wizard now**, and then select **Finish**.
4. Select **Action** &gt; **Install Licenses**. Enter your license code ready to enter when prompted.

### Activate using a web browser

1. On the **License Server Activation** page, copy the URL for the Remote Desktop Licensing Web Site. Then open a web browser and navigate to the site.
2. Complete the steps on the Remote Desktop Licensing Web Site.
3. Return to the **License Server Activation** page and enter in the **license server ID**. Select **Next**.

### Activate by telephone

1. Select your Country or Region. Then select **Next**.
2. On the **License Server Activation** page, call Microsoft at the number displayed. The representative provides you with a license server ID to enter. Select **Next**.