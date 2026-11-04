---
layout: Conceptual
title: Planning Your Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/planning-your-deployment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Planning Your Deployment'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 5c888601-1d8e-bf5f-e3b6-d377dd697340
document_version_independent_id: fc01eda6-02ea-a69b-54ef-a935b8f0b326
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Planning-Your-Deployment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/planning-your-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Planning-Your-Deployment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 33ed1379-587e-e589-4c2b-3775c5fc2c9a
---

# Planning Your Deployment | Microsoft Learn

When you plan for cross-organizational (federation-based) collaboration using Active Directory Federation Services (AD FS), first determine if your organization will host a Web resource to be accessed by other organizations across the Internet or if you will provide access to the Web resource for employees in your organization. This determination affects how you deploy AD FS, and it is fundamental in the planning of your AD FS infrastructure.

Note

Make sure that the role that organization plays in the federation agreement is clearly understood by all parties.

For the [Federated Web SSO Design](federated-web-sso-design), AD FS uses terms such as *account partner* (also referred to as *identity provider* in the AD FS Management snap-in) and *resource partner* (also referred to as *relying party* in the AD FS Management snap-in) to help differentiate the organization that hosts the accounts (the account partner) from the organization that hosts the Web-based resources (the resource partner).

In the [Web SSO Design](web-sso-design), the organization acts in both the account partner and resource partner roles because it is providing its users with access to its applications.

The following topics explain some of the AD FS partner organization concepts. They also contain links to topics in the AD FS Deployment Guide that contain information about setting up and configuring account partner organizations and resource partner organizations based on your AD FS deployment goals.