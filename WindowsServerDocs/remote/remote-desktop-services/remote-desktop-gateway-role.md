---
layout: Conceptual
title: Deploy Remote Desktop Gateway role for Remote Desktop Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/remote-desktop-gateway-role
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to deploy the Remote Desktop Gateway role for Remote Desktop Services.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-24T00:00:00.0000000Z
locale: en-us
document_id: 33676c07-7132-c660-0f4b-f4e3c8c664bb
document_version_independent_id: 48dc2696-ebd0-2933-9531-c79ca28b8837
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/remote-desktop-gateway-role.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/remote-desktop-gateway-role
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/remote-desktop-gateway-role.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 868c2024-03dd-d542-f416-c162c8367085
---

# Deploy Remote Desktop Gateway role for Remote Desktop Services | Microsoft Learn

The Remote Desktop Gateway (RD Gateway) role enables secure, encrypted connections to Remote Desktop Services (RDS) resources over the internet. With RD Gateway, users can access internal network resources from remote locations without the need for a VPN. You can deploy RD Gateway servers on either physical or virtual machines, supporting on-premises, cloud, or hybrid environments. This article guides you through installing and configuring the RD Gateway role to enhance the security and accessibility of your Remote Desktop environment.

## Prerequisites

Your device must have the **Remote Desktop Services** role installed. To learn more, see [Add or remove roles and features in Windows Server](/en-us/windows-server/administration/server-manager/add-remove-roles-features).

- During the installation process, select the **Remote Desktop Gateway** Role service, and proceed with installation.

Note

For this article, we're using default settings for installing the RD Gateway, progressing through without additional changes. Based on your own organizational needs, during the Role service selection for the Web Server Role (IIS), select the additional services necessary for your environment.

You must be a part of the **Administrators** group or have equivalent permissions.

## Configure the RD Gateway role

Once the RD Gateway role is installed, it needs to be configured. To configure the RD Gateway role, follow these steps:

1. In **Server Manager**, select **Remote Desktop Services**, then select **Servers**
2. Right-click the name of your server, then select **RD Gateway Manager**.
3. In the **RD Gateway Manager** on the left pane, right-click the name of your gateway, then select **Properties**.
4. Select the **SSL Certificate** tab, select the **Import a certificate into the RD Gateway** radio button, then select **Browse and Import Certificate**.
5. Locate and select your PFX file, then select **Open**.
6. Enter the password for the PFX file when prompted.

After you've imported the certificate and its private key, the display should show the certificate’s key attributes.

Note

Because the RD Gateway role is supposed to be public, we recommend you use a publicly issued certificate. If you use a privately issued certificate, you'll need to make sure to configure all clients with the certificate's trust chain beforehand.