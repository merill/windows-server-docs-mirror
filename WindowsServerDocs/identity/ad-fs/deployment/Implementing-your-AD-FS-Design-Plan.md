---
layout: Conceptual
title: Implementing Your AD FS Design Plan | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/implementing-your-ad-fs-design-plan
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Implementing Your AD FS Design Plan'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: e0e6b1cc-fa24-844c-4892-6923e2afbe95
document_version_independent_id: fa4f909b-a01e-54e4-8926-7346bbc3e108
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Implementing-your-AD-FS-Design-Plan.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/implementing-your-ad-fs-design-plan
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Implementing-your-AD-FS-Design-Plan.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: d34b4465-cb43-1123-499a-a6f552dfd5e6
---

# Implementing Your AD FS Design Plan | Microsoft Learn

The following environmental conditions and requirements are important factors in the implementation of your Active Directory Federation Services (AD FS) design plan:

- **Supported partners:** You usually use AD FS to work with partner organizations. To establish identity federation, determine the organizations with which you want to form a partnership. After a baseline AD FS deployment is in place, operating with partners involves adding partners, deleting partners, and updating partner information. Changes to partnerships may occur for a variety of reasons. For example, your AD FS deployment might require partnership updates if your partner changes its business significantly, your organization becomes part of a larger organization or a federation of organizations, or your organization is acquired by a different company. In any scenario in which you federate identities from multiple domains, you will need to know the domains (partners) that you are currently supporting and all the additional domains that represent potential partners.
- **Supported application and service types:** Some applications and services require access to operating system resources, while others are "claims aware." It is important to understand the types of applications and services that AD FS supports so that you can formulate administration requirements.
- **Logical and physical architectural diagrams or deployment topology:** You will need to know:

    - Whether federation servers will function in a set of farmed servers or on a single server.
    - Where your network deploys firewalls and proxies.
    - The location of resources and whether users are accessing resources from within your organization, outside the organization, or both.

## How to implement your AD FS design using this guide

The next step in implementing your design is to determine in what order each deployment task must be performed. This guide uses checklists to help you walk through the various server and application deployment tasks that are required to implement your design plan. Parent and child checklists are used as necessary to represent the order in which tasks for a specific AD FS design must be processed.

Use the following parent checklists in this section of the guide to become familiar with the deployment tasks for implementing your organization's preferred AD FS design:

- [Checklist: Implementing a Web SSO Design](checklist--implementing-a-web-sso-design)
- [Checklist: Implementing a Federated Web SSO Design](checklist--implementing-a-federated-web-sso-design)