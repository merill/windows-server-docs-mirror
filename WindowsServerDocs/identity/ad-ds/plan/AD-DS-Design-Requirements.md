---
layout: Conceptual
title: AD DS Design Requirements | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/ad-ds-design-requirements
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD DS Design Requirements'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: a590fbec-c6b6-bc2e-2f78-24608a804424
document_version_independent_id: f0584793-e034-1fe9-6ba2-1a2422a6ed94
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/AD-DS-Design-Requirements.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/ad-ds-design-requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/AD-DS-Design-Requirements.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f6c39657-5cec-4985-66dc-1e7914e99a72
---

# AD DS Design Requirements | Microsoft Learn

## Designing the Active Directory logical structure

Before you deploy Windows Server 2008 Active Directory Domain Services (AD DS), you must plan for and design the AD DS logical structure for your environment. The AD DS logical structure determines how your directory objects are organized, and it provides an effective method for managing your network accounts and shared resources. When you design your AD DS logical structure, you define a significant part of the network infrastructure of your organization.

To design the AD DS logical structure, determine the number of forests that your organization requires, and then create designs for domains, Domain Name System (DNS) infrastructure, and organizational units (OUs). The following illustration shows the process for designing the logical structure.

![Illustration that shows the process for designing the logical structure.](media/ad-ds-design-requirements/d5cebae6-a752-4063-a98f-473799c251bd.gif)

For more information, see [Designing the Logical Structure for Windows Server 2008 AD DS](designing-the-logical-structure).

## Designing the site topology

After you design the logical structure for your AD DS infrastructure, you must design the site topology for your network. The site topology is a logical representation of your physical network. It contains information about the location of AD DS sites, the AD DS domain controllers within each site, and the site links and site link bridges that support AD DS replication between sites. The following illustration shows the site topology design process.

![Illustration that shows the site topology design process.](media/ad-ds-design-requirements/d34d43c0-437f-47cb-9b64-09c0f9ce6479.gif)

For more information, see [Designing the Site Topology for Windows Server 2008 AD DS](designing-the-site-topology).

## Planning domain controller capacity

To ensure efficient AD DS performance, you must determine the appropriate number of domain controllers for each site and verify that they meet the hardware requirements for Windows Server 2008 . Careful capacity planning for your domain controllers ensures that you do not underestimate hardware requirements, which can cause poor domain controller performance and application response time. The following illustration shows the process of domain controller capacity planning.

![AD DS design requirements](media/ad-ds-design-requirements/fff6ef22-5c7b-4478-ad76-42b296dcf769.gif)

## Enabling Windows Server 2008 advanced AD DS features

You can use Windows Server 2008 AD DS to introduce advanced features into your environment by raising the domain or forest functional level. You can raise the functional level to Windows Server 2008 when all domain controllers in the domain or forest are running Windows Server 2008 .

For more information, see [Enabling Advanced Features for AD DS](enabling-advanced-features-for-ad-ds).