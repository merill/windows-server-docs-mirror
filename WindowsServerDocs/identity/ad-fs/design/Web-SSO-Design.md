---
layout: Conceptual
title: Web SSO Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/web-sso-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Web SSO Design'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 75333286-557c-89fb-ec03-03004b20ffed
document_version_independent_id: ce92afac-acd4-c77f-fd13-a1f5213530e9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Web-SSO-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/web-sso-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Web-SSO-Design.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 8eb7c4a8-e62a-1bc8-e851-1095090897e9
---

# Web SSO Design | Microsoft Learn

In the Web Single-Sign-On (SSO) design in Active Directory Federation Services (AD FS), users must authenticate only once to access multiple AD FS-secured applications or services. In this design all users are external, and no federation trust exists because there are no partner organizations. Typically, you deploy this design when you want to provide individual consumer or customer access to one or more AD FS–secured services or applications over the Internet, as shown in the following illustration.

![web sso design](media/adfs2_webssodesign.gif)

With the Web SSO design, an organization that typically hosts an AD FS-secured application or service in a perimeter network can maintain a separate store of customer accounts in the perimeter network, which makes it easier to isolate customer accounts from employee accounts.

You can manage the local accounts for customers in the perimeter network by using either Active Directory Domain Services (AD DS), SQL Server, or a custom attribute store.

This design coincides with the deployment goal in [Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](provide-your-active-directory-users-access-to-your-claims-aware-applications-and-services).

For a list of detailed tasks that you can use to plan and deploy your Web SSO design, see [Checklist: Implementing a Web SSO Design](../deployment/checklist--implementing-a-web-sso-design).