---
layout: Conceptual
title: STEP 2 Configure EDGE1 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-cluster-nlb/step-2-configure-edge1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to configure DirectAccess on the EDGE1 server.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 7dd98a21-e87f-c8d8-74c4-3450fa746ae4
document_version_independent_id: 99c3e0dd-42af-fe58-5fe2-528b712045ac
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-cluster-nlb/STEP-2-Configure-EDGE1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-cluster-nlb/step-2-configure-edge1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-cluster-nlb/STEP-2-Configure-EDGE1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 4670e336-5f87-1f9c-2af7-03bcf881a9c9
---

# STEP 2 Configure EDGE1 | Microsoft Learn

The following procedure is performed on the DirectAccess server:

## To configure DirectAccess on EDGE1

1. On the **Start** screen, type**RAMgmtUI.exe**, and then press ENTER. If the **User Account Control** dialog box appears, confirm that the action it displays is what you want, and then click **Yes**.
2. In the Remote Access Management console, in the left pane, click **Configuration**.
3. In the middle pane of the console, in the **Step 2 Remote Access Server** area, click **Edit**.
4. In the **Remote Access Server Setup** wizard, click **Prefix Configuration**. On the **Prefix Configuration** page, in **IPv6 prefix assigned to DirectAccess client computers**, enter **2001:db8:1:1000::/59**, and then click **Next**.
5. Click **Finish**.
6. In the middle pane of the console, click **Finish**.
7. On the **Remote Access Review** dialog box, review the configuration settings, and then click **Apply**. On the **Applying Remote Access Setup Wizard Settings** dialog box, click **Close**.