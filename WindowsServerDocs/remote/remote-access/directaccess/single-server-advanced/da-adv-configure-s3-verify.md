---
layout: Conceptual
title: Step 3 Verify the Advanced DirectAccess Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/single-server-advanced/da-adv-configure-s3-verify
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to verify that you have correctly configured your advanced DirectAccess deployment.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 9b08d342-487d-f1cd-6fec-78da7ccbf8c4
document_version_independent_id: a89cd6a3-ddf6-2b05-bbdb-445d3556fcca
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/single-server-advanced/da-adv-configure-s3-verify.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/single-server-advanced/da-adv-configure-s3-verify
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/single-server-advanced/da-adv-configure-s3-verify.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8c767fa2-30bd-7ef4-b6fb-fb2a678e09c7
---

# Step 3 Verify the Advanced DirectAccess Deployment | Microsoft Learn

This topic describes how to verify that you have correctly configured your DirectAccess deployment.

### To verify access to internal resources through DirectAccess

1. Connect a DirectAccess client computer to the corporate network and obtain the Group Policy Object.
2. Click the **Network connections** icon in the notification area to access the DirectAccess Media Manager.
3. Click **DirectAccess Connection**, and you will see that the status is **Connected Locally**.
4. Connect the client computer to the external network and attempt to access internal resources.

    You should be able to access all corporate resources.

## Previous step

- [Step 2: Configuring DirectAccess Servers](da-adv-configure-s2-servers)