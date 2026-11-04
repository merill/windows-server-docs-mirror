---
layout: Conceptual
title: Planning Federation Server Placement | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/planning-federation-server-placement
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Planning Federation Server Placement'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: ff27f0b9-73c0-7329-a0c0-5f5e4fbad3ec
document_version_independent_id: 30925e18-89ac-0f2d-c656-bf0faccf087f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Planning-Federation-Server-Placement.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/planning-federation-server-placement
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Planning-Federation-Server-Placement.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 62af604c-e200-64ad-7b4e-35f5e6678eb8
---

# Planning Federation Server Placement | Microsoft Learn

The most critical component of an Active Directory Federation Services (AD FS) deployment is the federation server. Therefore, it is important that you plan your federation server placement strategy carefully, including when and where to deploy federation servers. The information in the following topics can help you determine when and where to create a federation server or federation server farm and whether to use that federation server in the account partner role, the resource partner role, or both:

- [Review the Role of the Federation Server in the Account Partner](review-the-role-of-the-federation-server-in-the-account-partner)
- [Review the Role of the Federation Server in the Resource Partner](review-the-role-of-the-federation-server-in-the-resource-partner)
- [When to Create a Federation Server](when-to-create-a-federation-server)
- [Where to Place a Federation Server](where-to-place-a-federation-server)
- [When to Create a Federation Server Farm](when-to-create-a-federation-server-farm)
- [Certificate Requirements for Federation Servers](certificate-requirements-for-federation-servers)
- [Name Resolution Requirements for Federation Servers](name-resolution-requirements-for-federation-servers)

Note

Although this information might help with your placement planning for federation servers, it does not explain how to determine the proper number of federation servers and the hardware requirements for each AD FS design.

For examples of how a federation server can be placed in any of the two primary AD FS design scenarios, see [Mapping Your Deployment Goals to an AD FS Design](mapping-your-deployment-goals-to-an-ad-fs-design).