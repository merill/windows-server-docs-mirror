---
layout: Conceptual
title: Reviewing OU Design Concepts | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/reviewing-ou-design-concepts
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Reviewing OU Design Concepts'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: f7b785b5-2b5f-9ec0-d429-49e01d45b35e
document_version_independent_id: 350db306-e299-1206-4d5b-f6e76da396af
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Reviewing-OU-Design-Concepts.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/reviewing-ou-design-concepts
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Reviewing-OU-Design-Concepts.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b643e87f-97b8-6650-cc5a-4189d3cd13f1
---

# Reviewing OU Design Concepts | Microsoft Learn

The organizational unit (OU) structure for a domain includes the following:

- A diagram of the OU hierarchy
- A list of OUs
- For each OU:

    - The purpose for the OU
    - A list of users or groups that have control over the OU or the objects in the OU
    - The type of control that users and groups have over the objects in the OU

The OU hierarchy does not need to reflect the departmental hierarchy of the organization or group. OUs are created for a specific purpose, such as the delegation of administration, the application of Group Policy, or to limit the visibility of objects.

You can design your OU structure to delegate administration to individuals or groups within your organization that require the autonomy to manage their own resources and data. OUs represent administrative boundaries and enable you to control the scope of authority of data administrators.

For example, you can create an OU called ResourceOU and use it to store all the computer accounts that belong to the file and print servers managed by a group. Then, you can configure security on the OU so that only data administrators in the group have access to the OU. This prevents data administrators in other groups from tampering with the file and print server accounts.

You can further refine your OU structure by creating subtrees of OUs for specific purposes, such as the application of Group Policy or to limit the visibility of protected objects so that only certain users can see them. For example, if you need to apply Group Policy to a select group of users or resources, you can add those users or resources to an OU, and then apply Group Policy to that OU. You can also use the OU hierarchy to enable further delegation of administrative control.

While there is no technical limit to the number of levels in your OU structure, for manageability we recommend that you limit your OU structure to a depth of no more than 10 levels. There is no technical limit to the number of OUs on each level. Note that Active Directory Domain Services (AD DS)-enabled applications might have restrictions on the number of characters used in the distinguished name (that is, the full Lightweight Directory Access Protocol (LDAP) path to the object in the directory) or on the OU depth within the hierarchy.

The OU structure in AD DS is not intended to be visible to end users. The OU structure is an administrative tool for service administrators and for data administrators, and it is easy to change. Continue to review and update your OU structure design to reflect changes in your administrative structure and to support policy-based administration.