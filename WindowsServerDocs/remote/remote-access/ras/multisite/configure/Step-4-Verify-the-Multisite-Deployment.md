---
layout: Conceptual
title: Step 4 Verify the Multisite Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/multisite/configure/step-4-verify-the-multisite-deployment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to verify that you have correctly configured your Remote Access multisite deployment.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: b24947e7-81f9-bcc6-9134-f08ed01570c4
document_version_independent_id: fc6fdf2c-b8f8-ee85-1a1c-e42ab5c4049a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/multisite/configure/Step-4-Verify-the-Multisite-Deployment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/multisite/configure/step-4-verify-the-multisite-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/multisite/configure/Step-4-Verify-the-Multisite-Deployment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 15244994-5f32-c2d6-8aa0-363b9cf882ed
---

# Step 4 Verify the Multisite Deployment | Microsoft Learn

This topic describes how to verify that you have correctly configured your Remote Access multisite deployment.

### To verify access to internal resources through the multisite deployment

1. Connect a DirectAccess client computer to the corporate network and obtain the group policy.
2. Connect the client computer to the external network and attempt to access internal resources.

    You should be able to access all corporate resources.
3. Test connectivity through each server in the multisite deployment by turning off, or disconnecting from the external network, all but one of the Remote Access servers. On the client computer, attempt to access corporate resources. Repeat the test on a different multisite server. It may take up to 10 minutes for the client computer to connect to the new entry point. This is because probing is turned off for 10 minutes for an entry point after it is deemed unreachable, in order to optimize bandwidth and battery life. Alternatively, you can switch between the various entry-points manually by choosing the desired entry-point from the combo-box shown when executing **daprop.exe**.

    You should be able to access all corporate resources through each multisite server.
4. Connect a Windows 7® client computer to the corporate network and obtain the group policy.
5. Connect the Windows 7 client computer to the external network and attempt to access internal resources.

    You should be able to access all corporate resources.
6. Test connectivity for Windows 7 clients through each server in the multisite deployment by accessing the Active Directory Users and Computers console, and moving the client computer to the security group that corresponds to each server. After the changes have replicated throughout the domain, restart the client computer while connected to the corporate network to obtain the new group policy. Attempt to access corporate resources. Repeat the test on a different multisite server.

    You should be able to access all corporate resources through each multisite server.

    In a production environment this method may not be feasible due to the amount of time required for changes to replicate throughout the domain. You may want to force replication where possible. Testing can also be done from multiple different Windows 7 client computers that are already members of the different Windows 7 security groups in the multisite deployment.