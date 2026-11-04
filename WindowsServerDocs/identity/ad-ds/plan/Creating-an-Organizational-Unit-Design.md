---
layout: Conceptual
title: Creating an Organizational Unit Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/creating-an-organizational-unit-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Creating an Organizational Unit Design'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: e140cf51-417d-522c-0363-a5eebb289699
document_version_independent_id: d0f6d8d8-9dd4-9acb-73b5-362d1b1ab54f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Creating-an-Organizational-Unit-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/creating-an-organizational-unit-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Creating-an-Organizational-Unit-Design.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 8b90c15a-32cc-34ba-6021-9ab08e01f14c
---

# Creating an Organizational Unit Design | Microsoft Learn

Forest owners are responsible for creating organizational unit (OU) designs for their domains. Creating an OU design involves designing the OU structure, assigning the OU owner role, and creating account and resource OUs.

Initially, design your OU structure to enable delegation of administration. When the OU design is complete, you can create additional OU structures for the application of Group Policy to the users and computers and to limit the visibility of objects. For more information, see [Designing a Group Policy Infrastructure](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc786524%28v=ws.10%29).

## OU owner role

The forest owner designates an OU owner for each OU that you design for the domain. OU owners are data managers who control a subtree of objects in Active Directory Domain Services (AD DS). OU owners can control how administration is delegated and how policy is applied to objects within their OU. They can also create new subtrees and delegate administration of OUs within those subtrees.

Because OU owners do not own or control the operation of the directory service, you can separate ownership and administration of the directory service from ownership and administration of objects, reducing the number of service administrators who have high levels of access.

OUs provide administrative autonomy and the means to control visibility of objects in the directory. OUs provide isolation from other data administrators, but they do not provide isolation from service administrators. Although OU owners have control over a subtree of objects, the forest owner retains full control over all subtrees. This enables the forest owner to correct mistakes, such as an error in an access control list (ACL), and to reclaim delegated subtrees when data administrators are terminated.

## Account OUs and resource OUs

Account OUs contain user, group, and computer objects. Forest owners must create an OU structure to manage these objects and then delegate control of the structure to the OU owner. If you are deploying a new AD DS domain, create an account OU for the domain so that you can delegate control of the accounts in the domain.

Resource OUs contain resources and the accounts that are responsible for managing those resources. The forest owner is also responsible for creating an OU structure to manage these resources and for delegating control of that structure to the OU owner. Create resource OUs as needed based on the requirements of each group within your organization for autonomy in the management of data and equipment.

## Documenting the OU design for each domain

Assemble a team to design the OU structure that you use to delegate control over resources within the forest. The forest owner might be involved in the design process and must approve the OU design. You might also involve at least one service administrator to ensure that the design is valid. Other design team participants might include the data administrators who will work on the OUs and the OU owners who will be responsible for managing them.

It is important to document your OU design. List the names of the OUs that you plan to create. And, for each OU, document the type of OU, the OU owner, the parent OU (if applicable), and the origin of that OU.

For a worksheet to assist you in documenting your OU design, download Job\_Aids\_Designing\_and\_Deploying\_Directory\_and\_Security\_Services.zip from [Job Aids for Windows Server 2003 Deployment Kit](https://microsoft.com/download/details.aspx?id=9608) and open "Identifying OUs for Each Domain" (DSSLOGI\_9.doc).