---
layout: Conceptual
title: STEP 7 Test Connectivity When Returning to the Corpnet | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-cluster-nlb/step-7-test-connectivity-when-returning-to-the-corpnet
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to test connectivity when returning to the corpnet on CLIENT1.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 99cef0d3-f9ae-c838-76d5-b1dbb907c34c
document_version_independent_id: e369060f-799b-ba41-306d-37e1619d2b08
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-cluster-nlb/STEP-7-Test-Connectivity-When-Returning-to-the-Corpnet.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-cluster-nlb/step-7-test-connectivity-when-returning-to-the-corpnet
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-cluster-nlb/STEP-7-Test-Connectivity-When-Returning-to-the-Corpnet.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 468b93e3-6da9-808d-6fcd-22a1179c6a03
---

# STEP 7 Test Connectivity When Returning to the Corpnet | Microsoft Learn

Many of your users will move between remote locations and the corpnet, so it's important that when they return to the corpnet that they are able to access resources without having to make any configuration changes. Remote Access makes this possible because when the DirectAccess client returns to the corpnet, it is able to make a connection to the network location server. Once the HTTPS connection is successfully established to the network location server, the DirectAccess client disables the DirectAccess client configuration and uses a direct connection to corpnet.

### Test connectivity on CLIENT1

1. Shut down CLIENT1 and then unplug CLIENT1 from the Homenet subnet or virtual switch and connect it to the Corpnet subnet or virtual switch. Turn on CLIENT1, and log on as CORP\User1.
2. Open an elevated Windows PowerShell window, type **ipconfig /all**, and press ENTER. The output will indicate that CLIENT1 has a local IP address, and that there is no active 6to4, Teredo, or IP-HTTPS tunnel.
3. Test connectivity to the network share on APP2. On the **Start** screen, type**\\APP2\Files**, and then press ENTER. You will be able to open the file in that folder.