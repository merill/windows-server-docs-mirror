---
layout: Conceptual
title: Configuring Partner Organizations | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/configuring-partner-organizations
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configuring Partner Organizations'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 780be1dc-3068-b401-1b31-987ba063ea66
document_version_independent_id: 79ecf54a-5110-963f-52d7-3df0c190231b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Configuring-Partner-Organizations.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/configuring-partner-organizations
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Configuring-Partner-Organizations.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 3d89f05a-40e3-b321-edb8-3477a45e3a74
---

# Configuring Partner Organizations | Microsoft Learn

To deploy a new partner organization in Active Directory Federation Services (AD FS), complete the tasks in either [Checklist: Configuring the Resource Partner Organization](checklist--configuring-the-resource-partner-organization) or [Checklist: Configuring the Account Partner Organization](checklist--configuring-the-account-partner-organization), depending on your AD FS design.

Note

When you use either of these checklists, we strongly recommend that you first read the references to account partner or resource partner planning guidance in the [AD FS Design Guide in Windows Server 2012](../design/ad-fs-design-guide-in-windows-server-2012) before continuing to the procedures for setting up the new partner organization. Following the checklist in this way will help provide a better understanding of the full AD FS design and deployment story for the account partner or resource partner organization.

## About account partner organizations

An account partner is the organization in the federation trust relationship that physically stores user accounts in an AD FS–supported attribute store. The account partner is responsible for collecting and authenticating a user's credentials, building up claims for that user, and packaging the claims into security tokens. These tokens can then be presented across a federation trust to enable access to Web-based resources that are located in the resource partner organization.

In other words, an account partner represents the organization for whose users the account-side federation server issues security tokens. The federation server in the account partner organization authenticates local users and creates security tokens that the resource partner uses in making authorization decisions.

With regard to attribute stores, the account partner in AD FS is conceptually equivalent to a single Active Directory forest whose accounts need access to resources that are physically located in another forest. Accounts in this forest can access resources in the resource forest only when an external trust or forest trust relationship exists between the two forests and the resources to which the users are trying to gain access have been set with the proper authorization permissions.

## About resource partner organizations

The resource partner is the organization in an AD FS deployment where Web servers are located. The resource partner trusts the account partner to authenticate users. Therefore, to make authorization decisions, the resource partner consumes the claims that are packaged in security tokens that come from users in the account partner.

In other words, a resource partner represents the organization whose Web servers are protected by the resource-side federation server. The federation server at the resource partner uses the security tokens that are produced by the account partner to make authorization decisions for Web servers in the resource partner.

To function as an AD FS resource, Web servers in the resource partner organization must either have Windows Identity Foundation (WIF) installed or have the Active Directory Federation Services (AD FS) 1.x Claims-Aware Web Agent role services installed. Web servers that function as an AD FS resource can host either Web-browser-based or Web-service-based applications.