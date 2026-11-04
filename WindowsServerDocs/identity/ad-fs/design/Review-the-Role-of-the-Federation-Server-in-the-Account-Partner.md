---
layout: Conceptual
title: Review the Role of the Federation Server in the Account Partner | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/review-the-role-of-the-federation-server-in-the-account-partner
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Review the Role of the Federation Server in the Account Partner'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 2b93b571-362a-eea5-1322-09cba1bf44bd
document_version_independent_id: 4f3c4af1-6d31-550c-6430-4d73c98230d0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Review-the-Role-of-the-Federation-Server-in-the-Account-Partner.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/review-the-role-of-the-federation-server-in-the-account-partner
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Review-the-Role-of-the-Federation-Server-in-the-Account-Partner.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: dd75123c-e72c-9e2c-81f4-1e6175accd2d
---

# Review the Role of the Federation Server in the Account Partner | Microsoft Learn

A federation server in Active Directory Federation Services (AD FS) functions as a security token issuer. A federation server generates claims based on account values that reside in a local attribute store and packages them into security tokens so that users can seamlessly access Web-browser-based applications (using single sign-on (SSO)) that are hosted in a resource partner organization.

Note

When your users access federated applications by using a Web browser, a federation server automatically issues cookies to the users to maintain their logon status for that Web-browser-based application. These cookies include claims for the users. The cookies enable SSO capabilities so that the users do not have to enter credentials each time that they visit different Web-browser-based applications in the resource partner.

In the Web SSO design, organizations with a perimeter network that want Internet users to have access to applications must install a federation server proxy in the perimeter network. In the Federated Web SSO design, there must be at least one federation server installed in the corporate network of the account partner organization and at least one federation server installed in the corporate network of the resource partner organization.

Note

Before you can set up a federation server computer in the account partner organization, you must first join the computer to any domain in the Active Directory forest where the federation server will be used to authenticate users from that forest. For more information, see [Checklist: Setting Up a Federation Server](../deployment/checklist--setting-up-a-federation-server).