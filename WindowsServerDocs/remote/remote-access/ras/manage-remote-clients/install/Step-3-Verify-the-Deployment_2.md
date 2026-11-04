---
layout: Conceptual
title: Step 3 Verify the Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/manage-remote-clients/install/step-3-verify-the-deployment_2
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to verify that you've correctly configured your deployment for remote management of DirectAccess clients.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 158c99db-ba59-f6f2-fb1a-22864d1889a4
document_version_independent_id: 80a5c525-07c6-b048-5e01-623f84c6ac45
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/manage-remote-clients/install/Step-3-Verify-the-Deployment_2.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/manage-remote-clients/install/step-3-verify-the-deployment_2
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/manage-remote-clients/install/Step-3-Verify-the-Deployment_2.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 69b0919b-5859-93c8-3ee4-214e07b4d8d3
---

# Step 3 Verify the Deployment | Microsoft Learn

This article describes how to verify that you've correctly configured your deployment for remote management of DirectAccess clients.

## To verify proper deployment

1. Connect a DirectAccess client computer to the corporate network and obtain the Group Policy Object.
2. On the client computer, select the **Network connections** icon in the notification area to access the DirectAccess Media Manager.
3. Select **DirectAccess Connection**. You'll see that the status is **Locally Connected**.
4. Remove the computer from the corporate network and connect it to a public network.
5. In the command prompt, type **nltest /dsgetdc: [fully qualified domain name]**. This command verifies that the corporate network is accessible to the client. If the domain controller isn't accessible, the error message ERROR\_NO\_SUCH\_DOMAIN will display, reporting that the domain doesn't exist.