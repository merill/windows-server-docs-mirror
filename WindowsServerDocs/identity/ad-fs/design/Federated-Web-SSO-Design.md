---
layout: Conceptual
title: Federated Web SSO Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/federated-web-sso-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Federated Web SSO Design'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: c23e405b-0047-d38e-d217-996822826982
document_version_independent_id: 87726512-d83f-2800-8dab-568067f98e39
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Federated-Web-SSO-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/federated-web-sso-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Federated-Web-SSO-Design.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 35d6dfa2-323d-9b50-ec2c-4cb946a6d2e2
---

# Federated Web SSO Design | Microsoft Learn

The Federated Web Single-Sign-On (SSO) design in Active Directory Federation Services (AD FS) involves secure communication that spans multiple firewalls, perimeter networks, and name-resolution servers—in addition to the entire Internet routing infrastructure.

Typically, this design is used when two organizations agree to create a federation trust relationship to allow users in one organization (the account partner organization) to access Web-based applications or services, which are secured by AD FS, in the other organization (the resource partner organization).

In other words, a federation trust relationship is the embodiment of a business-level agreement or partnership between two organizations. As shown in the following illustration, you can establish a federation trust relationship between two businesses, which results in an end-to-end federation scenario.

![federated web sso](media/adfs2_federatedwebssodesign.gif)

The one-way arrow in the illustration signifies the direction of the federation trust, which—like the direction of Windows trusts—always points to the account side of the forest. This means that authentication flows from the account partner organization to the resource partner organization.

In this Federated Web SSO design, two federation servers (one in Fabrikam and the other in Contoso) route authentication requests from user accounts in Fabrikam to Web-based applications or services in Contoso.

Note

For additional security, you can use federation server proxies to relay requests to federation servers that are not directly accessible from the Internet.

In this example, Fabrikam is the identity, or account, provider. The Fabrikam portion of the Federated Web SSO design uses the following AD FS deployment goal:

- [Provide Your Active Directory Users Access to the Applications and Services of Other Organizations](provide-your-active-directory-users-access-to-the-applications-and-services-of-other-organizations)

Contoso is the resource provider. The Contoso portion of the Federated Web SSO design achieves the following AD FS deployment goals:

- [Provide Users in Another Organization Access to Your Claims-Aware Applications and Services](provide-users-in-another-organization-access-to-your-claims-aware-applications-and-services)
- [Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](provide-your-active-directory-users-access-to-your-claims-aware-applications-and-services)

For a list of detailed tasks that you can use to plan and deploy the Federated Web SSO design, see [Checklist: Implementing a Federated Web SSO Design](../deployment/checklist--implementing-a-federated-web-sso-design).