---
layout: Conceptual
title: Mapping Your Deployment Goals to an AD FS Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/mapping-your-deployment-goals-to-an-ad-fs-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Mapping Your Deployment Goals to an AD FS Design'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: install-set-up-deploy
locale: en-us
document_id: 6f226d77-f336-f965-54f0-3a8077460496
document_version_independent_id: ae9fc61a-1b13-9533-8682-f2fea3956305
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Mapping-Your-Deployment-Goals-to-an-AD-FS-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/mapping-your-deployment-goals-to-an-ad-fs-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Mapping-Your-Deployment-Goals-to-an-AD-FS-Design.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: e0936285-b500-c4f7-9b03-d626de5744c9
---

# Mapping Your Deployment Goals to an AD FS Design | Microsoft Learn

After you finish reviewing the existing Active Directory Federation Services (AD FS) deployment goals and you determine which goals are related to your deployment, you can map those goals to a specific AD FS design. For more information about AD FS predefined deployment goals, see [Identifying Your AD FS Deployment Goals](identifying-your-ad-fs-deployment-goals).

Use the following table to determine which AD FS design maps to the appropriate combination of AD FS deployment goals for your organization. This table refers only to the two primary AD FS designs, as described in this guide. However, you can create a hybrid or custom AD FS design by using any combination of the AD FS deployment goals to meet the needs of your organization.

| AD FS deployment goal | [Web SSO Design](web-sso-design) | [Federated Web SSO Design](federated-web-sso-design) |
| --- | --- | --- |
| [Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](provide-your-active-directory-users-access-to-your-claims-aware-applications-and-services) | No | Yes, in the account partner |
| [Provide Your Active Directory Users Access to the Applications and Services of Other Organizations](provide-your-active-directory-users-access-to-the-applications-and-services-of-other-organizations) | No | Yes, optional in the account partner |
| [Provide Users in Another Organization Access to Your Claims-Aware Applications and Services](provide-users-in-another-organization-access-to-your-claims-aware-applications-and-services) | Yes | Yes |