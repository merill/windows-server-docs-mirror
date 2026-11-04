---
layout: Conceptual
title: Install the Web Server WEB1 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/server-certs/install-the-web-server-web1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to install the Web Server (IIS) server role.
ms.topic: tutorial
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 021059e3-0b8b-aec2-b6eb-9cde6e8b3897
document_version_independent_id: 2fab2a3d-fa3f-1dff-461f-94787008b933
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Install-the-Web-Server-WEB1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/server-certs/install-the-web-server-web1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Install-the-Web-Server-WEB1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 84e89fc9-9a35-0ad5-4b4d-8efe89439506
---

# Install the Web Server WEB1 | Microsoft Learn

The Web Server (IIS) role in Windows Server 2016 provides a secure, easy-to-manage, modular and extensible platform for reliably hosting websites, services, and applications. With IIS, you can share information with users on the Internet, an intranet, or an extranet. IIS is a unified web platform that integrates IIS, ASP.NET, FTP services, PHP, and Windows Communication Foundation (WCF).

When you deploy server certificates, your Web server provides you with a location where you can publish the certificate revocation list (CRL) for your certification authority (CA). After publication, the CRL is accessible to all computers on your network so that they can use this list during the authentication process to verify that certificates presented by other computers are not revoked.

If a certificate is on the CRL as revoked, the authentication effort fails and your computer is protected from trusting an entity that has a certificate that is no longer valid.

Before you install the Web Server (IIS) role, ensure that you have configured the server name and IP address and have joined the computer to the domain.

## To install the Web Server (IIS) server role

To complete this procedure, you must be a member of the **Administrators** group.

Note

To perform this procedure by using Windows PowerShell, open PowerShell, type the following command, and then press ENTER. `Install-WindowsFeature Web-Server -IncludeManagementTools`

1. In Server Manager, click **Manage**, and then click **Add Roles and Features**. The Add Roles and Features Wizard opens.
2. In **Before You Begin**, click **Next**.

**Note** The **Before You Begin** page of the Add Roles and Features Wizard is not displayed if you have previously run the Add Roles and Features Wizard and you selected **Skip this page by default** at that time.

1. On the **Installation Type** page, click **Next**.
2. On the **Server selection** page, click **Next**.
3. On the **Server roles** page, select **Web Server (IIS)**, and then click **Next**.
4. Click **Next** until you have accepted all of the default web server settings, and then click **Install**.
5. Verify that all installations were successful, and then click **Close**.