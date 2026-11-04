---
layout: Conceptual
title: Planning Federation Server Proxy Placement | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/planning-federation-server-proxy-placement
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Planning Federation Server Proxy Placement'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: e8c0730f-cf68-4a64-07ea-4ed469363100
document_version_independent_id: 1e108d26-06d5-49aa-426c-8258ba5b86e7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Planning-Federation-Server-Proxy-Placement.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/planning-federation-server-proxy-placement
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Planning-Federation-Server-Proxy-Placement.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: fa4e764e-7a2e-9807-4ae6-21a4b82cccc5
---

# Planning Federation Server Proxy Placement | Microsoft Learn

After you gather all the information that you will use to design your Active Directory Federation Services (AD FS) infrastructure and after you plan your federation server and Web server strategy, you can plan when and where to place federation server proxies in your new design. The information in the following topics can help you determine when and where to place a federation server proxy and whether to configure it for the account partner role or the resource partner role:

- [Review the Role of the Federation Server in the Account Partner](review-the-role-of-the-federation-server-in-the-account-partner)
- [Review the Role of the Federation Server Proxy in the Resource Partner](review-the-role-of-the-federation-server-proxy-in-the-resource-partner)
- [When to Create a Federation Server Proxy](when-to-create-a-federation-server-proxy)
- [Where to Place a Federation Server Proxy](where-to-place-a-federation-server-proxy)
- [When to Create a Federation Server Proxy Farm](when-to-create-a-federation-server-proxy-farm)
- [Certificate Requirements for Federation Server Proxies](certificate-requirements-for-federation-server-proxies)
- [Name Resolution Requirements for Federation Server Proxies](name-resolution-requirements-for-federation-server-proxies)

Note

Although this information might help with your placement planning for federation server proxies, it does not explain how to determine the proper number of proxies and the proxy hardware requirements for each AD FS design.

For examples of how you can place a federation server proxy in either of the two primary AD FS design scenarios, see [Mapping Your Deployment Goals to an AD FS Design](mapping-your-deployment-goals-to-an-ad-fs-design).