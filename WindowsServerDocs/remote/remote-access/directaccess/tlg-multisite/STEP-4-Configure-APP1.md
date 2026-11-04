---
layout: Conceptual
title: STEP 4 Configure APP1 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-multisite/step-4-configure-app1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to configure the default gateway and DNS server.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 7c6785dd-c39e-e71f-d077-feebf0ef62fc
document_version_independent_id: 7abb2143-9b9c-85ed-49bc-86f375d16e28
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/STEP-4-Configure-APP1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-multisite/step-4-configure-app1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/STEP-4-Configure-APP1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8c266f37-9972-dc43-b0d7-303b37775349
---

# STEP 4 Configure APP1 | Microsoft Learn

Configure static IPv6 addressing and gateway settings to enable APP1 access to the 2-Corpnet subnet.

- To configure the default gateway and DNS server. The multisite configuration uses the ROUTER1 computer as a default gateway. Configure the default gateway on APP1.

## To configure the default gateway and DNS server

1. In the Server Manager console, click **Local Server**, and then in the **Properties** area, next to **Wired Ethernet Connection**, click the link.
2. In the **Network Connections** window, right-click **Wired Ethernet Connection**, and then click **Properties**.
3. On the **Wired Ethernet Connection Properties** dialog box, click **Internet Protocol Version 4 (TCP/IPv4)**, and then click **Properties**.
4. In **Default gateway**, type **10.0.0.254**, and in **Alternate DNS server**, type **10.2.0.1**, and then click **OK**.
5. On the **Wired Ethernet Connection Properties** dialog box, click **Internet Protocol Version 6 (TCP/IPv6)**, and then click **Properties**.
6. In **Default gateway**, type **2001:db8:1::fe**. In **Alternate DNS server**, type **2001:db8:2::1**, and then click **OK**.
7. On the **Wired Ethernet Connection Properties** dialog box, click **Close**, and then close the **Network Connections** window.