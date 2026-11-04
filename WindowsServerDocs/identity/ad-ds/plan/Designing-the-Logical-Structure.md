---
layout: Conceptual
title: Designing the Logical Structure | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/designing-the-logical-structure
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Designing the Logical Structure'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: b2e9d655-d7f8-64d2-0969-4f0f241fd223
document_version_independent_id: 9a5bf83f-5d07-f952-6a96-042e512e2d7f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Designing-the-Logical-Structure.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/designing-the-logical-structure
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Designing-the-Logical-Structure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: b5a5073d-fe43-6609-f5c0-f6f71032dfbd
---

# Designing the Logical Structure | Microsoft Learn

Active Directory Domain Services (AD DS) enables organizations to create a scalable, secure, and manageable infrastructure for user and resource management. It also enables them to support directory-enabled applications.

A well-designed Active Directory logical structure provides the following benefits:

- Simplified management of Microsoft Windows-based networks that contain large numbers of objects
- A consolidated domain structure and reduced administration costs
- The ability to delegate administrative control over resources, as appropriate
- Reduced impact on network bandwidth
- Simplified resource sharing
- Optimal search performance
- Low total cost of ownership

A well-designed Active Directory logical structure facilitates the efficient integration of such features as Group Policy; desktop lockdown; software distribution; and user, group, workstation, and server administration into your system. In addition, a carefully designed logical structure facilitates the integration of Microsoft and non-Microsoft applications and services, such as Microsoft Exchange Server, public key infrastructure (PKI), and a domain-based distributed file system (DFS).

When you design an Active Directory logical structure before you deploy AD DS, you can optimize your deployment process to best take advantage of Active Directory features. To design the Active Directory logical structure, your design team first identifies the requirements for your organization and, based on this information, decides where to place the forest and domain boundaries. Then, the design team decides how to configure the Domain Name System (DNS) environment to meet the needs of the forest. Finally, the design team identifies the organizational unit (OU) structure that is required to delegate the management of resources in your organization.

## In this guide

- [Understanding the Active Directory Logical Model](understanding-the-active-directory-logical-model)
- [Identifying the Deployment Project Participants](identifying-the-deployment-project-participants)
- [Creating a Forest Design](creating-a-forest-design)
- [Creating a Domain Design](creating-a-domain-design)
- [Creating a DNS Infrastructure Design](creating-a-dns-infrastructure-design)
- [Creating an Organizational Unit Design](creating-an-organizational-unit-design)
- [Appendix A: DNS Inventory](appendix-a--dns-inventory)