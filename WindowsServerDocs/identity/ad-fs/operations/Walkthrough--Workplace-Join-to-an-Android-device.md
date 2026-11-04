---
layout: Conceptual
title: Walkthrough - Workplace Join to an Android device | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/walkthrough--workplace-join-to-an-android-device
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Walkthrough: Workplace Join to an Android device'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 26b16838-e4e9-12be-ad34-6c476f6537a4
document_version_independent_id: 5c17031a-5e93-27de-e032-3cce1949a988
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Walkthrough--Workplace-Join-to-an-Android-device.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/walkthrough--workplace-join-to-an-android-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Walkthrough--Workplace-Join-to-an-Android-device.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/5686b492-7c45-4088-8291-ecc0458747d3
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/838f4f15-80c1-4d49-b873-501fe4ed2d28
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: db9ced2c-36d0-f89d-b55f-c77e6df72220
---

# Walkthrough - Workplace Join to an Android device | Microsoft Learn

## Join your device with Workplace Join

Note

Android workplace join requires Microsoft Entra Device Registration Service. In order to enforce conditional device policies on-premises, Directory Synchronization Tool (DirSync) must be deployed with device object write-back option enabled. At the present time, device write-back to Active Directory from Microsoft Entra ID can take up-to 3 hours. As such, users must wait for 3 hours to access on-premises web applications, after creating a work account. For more information about deploying Microsoft Entra Device Registration service, see, [Microsoft Entra Device Registration Service Overview](/en-us/previous-versions/azure/dn788908%28v=azure.100%29)

#### Create a Work account that joins your device with workplace Join

1. You will need to install Azure Authenticator application on your device to create a work account that joins your device with Workplace join. The following URL has instructions on how to install Azure authenticator app on your Android device and add a work account. The work account makes your Android device into a trusted device and provides Single Sign-On (SSO) to the applications on device. You can use the trusted device to access web applications and modern line-of-business applications as recommended by your IT administrator. For more information, see [Azure Authenticator for Android](/en-us/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to).