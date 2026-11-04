---
layout: Conceptual
title: STEP 9 Configure EDGE1 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-multisite/step-9-configure-edge1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to configure the DNS servers on EDGE1 and configure routing between subnets.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 6416dd39-288d-d587-2d9f-e659367b1cdb
document_version_independent_id: f48a91b2-7e97-4fd9-a09a-e07edb2ad6e3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/STEP-9-Configure-EDGE1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-multisite/step-9-configure-edge1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/STEP-9-Configure-EDGE1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 76cb43cc-5a64-b78a-9a5d-3fb880214577
---

# STEP 9 Configure EDGE1 | Microsoft Learn

The following procedures are performed on the EDGE1 server:

1. Configure the DNS servers on EDGE1. It is necessary to configure the DNS server from the corp2.corp.contoso.com domain on EDGE1.
2. Configure routing between subnets. Configure routing on EDGE1 to enable communication between the Corpnet and 2-Corpnet subnets.

## Configure the DNS servers on EDGE1

1. In the Server Manager console, click **Local Server**, and then in the **Properties** area, next to **Corpnet**, click the link.
2. In the Network Connections window, right-click **Corpnet**, and then click **Properties**.
3. Click **Internet Protocol Version 4 (TCP/IPv4)**, and then click **Properties**.
4. In **Alternate DNS server**, type **10.2.0.1**. and then click **OK**.
5. Click **Internet Protocol Version 6 (TCP/IPv6)**, and then click **Properties**.
6. In **Alternate DNS server**, type **2001:db8:2::1** and then click **OK**.
7. On the **Corpnet Properties** dialog box, click **Close**.
8. Close the **Network Connections** window.

## Configure routing between subnets

1. On the **Start** screen, type**cmd.exe**, right-click **cmd**, click **Advanced**, and then click **Run as administrator**. If the **User Account Control** dialog box appears, confirm that the action it displays is what you want, and then click **Yes**.
2. In the Command Prompt window, enter the following commands. After entering each command, press ENTER.

    ```
    netsh interface IPv4 add route 10.2.0.0/24 Corpnet 10.0.0.254
    netsh interface IPv6 add route 2001:db8:2::/64 Corpnet 2001:db8:1::fe
    ```
3. Close the Command Prompt window.