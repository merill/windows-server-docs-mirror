---
layout: Conceptual
title: Reactivate or deactivate the Remote Desktop Services license server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/remote-desktop-services-reactivate-deactivate-license-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Reactivate or deactivate the Remote Desktop Services license server.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: 83ac3668-f2ed-5297-9185-bbc0da60dd82
document_version_independent_id: 83ac3668-f2ed-5297-9185-bbc0da60dd82
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/remote-desktop-services-reactivate-deactivate-license-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/remote-desktop-services-reactivate-deactivate-license-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/remote-desktop-services-reactivate-deactivate-license-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 46ba9dee-7587-294b-75c1-ceb691016a54
---

# Reactivate or deactivate the Remote Desktop Services license server | Microsoft Learn

In this article learn how-to reactivate or deactivate a Remote Desktop Services license server automatically over the internet, using a web browser, or by telephone.

## Prerequisites

Consider the following prerequisites before either reactivating or deactivating the license server:

- You'll need to know which server is the license server.
- You'll need membership in the **Administrators** group, or equivalent.

## Reactive a license server

You must reactivate a Remote Desktop license server when any of the following occur:

- The license server certificate expired.
- The license server certificate was corrupted.
- The license server was upgraded.
- The license server was redeployed.
- The license server private key was compromised.

Reactivate a license server by using one of the following methods:

- Reactivate a license server automatically
- Reactivate a license server using a web browser
- Reactivate a license server by telephone

### Reactivate a license server automatically

The automatic reactivation method requires internet connectivity from the computer running the Remote Desktop Licensing Manager tool. Complete the following steps to reactivate a license server automatically:

1. In Server Manager, select **Tools** &gt; **Remote Desktop Services** &gt; **Remote Desktop Licensing Manager**.
2. In RD Licensing Manager, verify that the connection method for the license server is set to **Automatic connection (recommended)**. To do this, right-click the license server that you want to reactivate, and then select **Properties**. On the **Connection Method** tab, change the connection method if necessary.
3. Right-click the license server that you want to reactivate, point to **Advanced**, and then select **Reactivate Server**. The Reactivate Server Wizard starts.
4. On the **Welcome** page, select **Next**.
5. On the **Information Needed** page, provide the requested information, and then select **Next**.
6. Your request to reactivate the license server is sent to the Microsoft Clearinghouse for processing, and the license server is reactivated.
7. On the Completing the Reactivate Server Wizard page, select **Finish**.

### Reactivate a license server using a web browser

The web reactivation method can be used when the computer running the Remote Desktop Licensing Manager tool doesn't have internet connectivity, but you have access to the web from another computer. The URL for the web method is displayed in the Reactivate Server Wizard.

To reactivate a Remote Desktop Licensing Manager server by using a web browser, complete the following steps:

1. In Server Manager, select **Tools** &gt; **Remote Desktop Services** &gt; **Remote Desktop Licensing Manager**.
2. Verify that the connection method for the Remote Desktop license server is set to **Web Browser** by right-clicking the license server that you want to reactivate, and then select **Properties**.
3. Using a computer that has internet connectivity, connect to the Remote Desktop Licensing website.
4. On the Remote Desktop Licensing website, select the option to **Reactivate a license server** and then select **Next**. Follow the steps to reactivate the license server.

### Reactivate a license server by telephone

The telephone reactivation method allows you to talk to a Microsoft customer service representative to complete the reactivation process. The appropriate telephone number depends on the country/region that is configured for the Remote Desktop Licensing Manager, and that telephone number is displayed in the Reactivate Server Wizard.

To reactivate a Remote Desktop Licensing Manager server by telephone, complete the following steps:

1. In Server Manager, select **Tools** &gt; **Remote Desktop Services** &gt; **Remote Desktop Licensing Manager**.
2. Verify that the connection method for the Remote Desktop license server is set to **Telephone** by right-clicking the license server that you want to reactivate, and then select **Properties**. On the **Connection Method** tab, change the connection method, if necessary, ensure that the correct country or region is selected in the Select Country or Region list, and then select **OK**.
3. Right-click the license server that you want to reactivate, point to **Advanced**, and then select **Reactivate Server**. The Reactivate Server Wizard starts.
4. On the **Welcome** page, select **Next**.
5. Call Microsoft by using the telephone number that is displayed on the **License Server Reactivation** page, and then provide the Microsoft customer support representative with the product ID and license server ID that is displayed on your screen.
6. The representative processes your request to reactivate the license server, and provides you with a new license server ID. On the **License Server Reactivation** page in the Reactivate Server Wizard, type the new license server ID that the representative provides, and then select **Next**. The license server is reactivated.
7. On the **Completing the Reactivate Server Wizard** page, select **Finish**.

## Deactive a license server

You may have to deactivate a license server if the certificate of the server expires, gets damaged, or if you redeploy the server.

The following steps describe how to deactivate a license server:

1. In Server Manager, select **Tools** &gt; **Remote Desktop Services** &gt; **Remote Desktop Licensing Manager**.
2. In the console tree, right-click the license server that you want to deactivate, select **Advanced**, and then select **Deactivate Server**.
3. In the Deactivate Server Wizard, confirm that your name, your phone number (optional), and your e-mail address that are listed under Information Needed are correct. Then select **Next**. Your request to deactivate the license server is sent to Microsoft Clearinghouse for processing.

    Note

    Your e-mail address is required if you are using the Internet method.
4. Select Finish.

When you deactivate a license server, you can't license other client computers from this server until the license server is activated again.