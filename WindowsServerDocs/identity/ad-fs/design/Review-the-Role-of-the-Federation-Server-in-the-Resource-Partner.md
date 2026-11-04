---
layout: Conceptual
title: Review the Role of the Federation Server in the Resource Partner | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/review-the-role-of-the-federation-server-in-the-resource-partner
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Review the Role of the Federation Server in the Resource Partner'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: b76e2b00-97f8-fe8a-84d7-a8103254902c
document_version_independent_id: 249ea951-19be-6555-5815-864bbceca57f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Review-the-Role-of-the-Federation-Server-in-the-Resource-Partner.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/review-the-role-of-the-federation-server-in-the-resource-partner
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Review-the-Role-of-the-Federation-Server-in-the-Resource-Partner.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: b41fed6a-26dd-1d26-60cc-7e20e19f5fba
---

# Review the Role of the Federation Server in the Resource Partner | Microsoft Learn

The federation server in the resource partner organization intercepts incoming security tokens that are sent by an account federation server, validates and signs them, and then issues its own security tokens that are destined for the Web-based application.

Note

When federated users use their Web browsers to access Web-based applications, the federation server in the resource partner organization builds a new authentication cookie and writes it to the browser. This cookie enables single-sign-on (SSO) capabilities so that users do not have to log on again at the federation server in the account partner when the users attempt to access different Web-based applications in the resource partner.

In the Web SSO design, at least one federation server must be installed in the perimeter network. In the Federated Web SSO design, there must be at least one federation server installed in the corporate network of the account partner organization and at least one federation server installed in the corporate network of the resource partner organization.

Note

Before you can set up a federation server computer in the resource partner organization, you must first join the computer to any Active Directory domain in the resource partner organization. For more information, see [Checklist: Setting Up a Federation Server](../deployment/checklist--setting-up-a-federation-server).