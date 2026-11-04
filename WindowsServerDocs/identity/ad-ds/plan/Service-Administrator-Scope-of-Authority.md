---
layout: Conceptual
title: Service Administrator Scope of Authority | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/service-administrator-scope-of-authority
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Service Administrator Scope of Authority'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: b6f666d5-547f-7b6f-f093-fa10a8fc34b3
document_version_independent_id: b7966fc9-443e-2562-1816-5d580bec8f7c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Service-Administrator-Scope-of-Authority.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/service-administrator-scope-of-authority
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Service-Administrator-Scope-of-Authority.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 7861ed79-1f42-d251-3e45-70e1d7edd57e
---

# Service Administrator Scope of Authority | Microsoft Learn

If you choose to participate in an Active Directory forest, you must trust the forest owner and the service administrators. The forest owners are responsible for selecting and managing the service administrators; therefore, when you trust a forest owner, you also trust the service administrators that the forest owner manages. These service administrators have access to all of the resources in the forest. Before making the decision to participate in a forest, it is important to understand that the forest owner and the service administrators will have full access to your data. You cannot prevent this access.

All service administrators in a forest have full control over all data and services on all computers in the forest. Service administrators have the capability to do the following:

- Correct errors on access control lists (ACLs) of objects. This enables the service administrator to read, modify, or delete objects regardless of the ACLs that are set on those objects.
- Modify the system software on a domain controller to bypass normal security checks. This enables the service administrator to view or manipulate any object in the domain, regardless of the ACL on the object.
- Use the Restricted Groups security policy to grant to any user or group administrative access to any computer joined to the domain. In this way, service administrators can obtain control of any computer joined to the domain regardless of the intentions of the computer owner.
- Reset passwords or change group memberships for users.
- Gain access to other domains in the forest by modifying the system software on a domain controller. Service administrators can affect the operation of any domain in the forest, view or manipulate forest configuration data, view or manipulate data stored in any domain, and view or manipulate data stored on any computer joined to the forest.

For this reason, groups that store data in organizational units (OUs) in the forest and that join computers to a forest must trust the service administrators. For a group to join a forest, it must choose to trust all service administrators in the forest. This involves ensuring that:

- The forest owner can be trusted to act in the interests of the group and does not have reason to act maliciously against the group.
- The forest owner appropriately restricts physical access to domain controllers. Domain controllers within a forest cannot be isolated from one another. It is possible for an attacker who has physical access to a single domain controller to make offline changes to the directory database and, by doing so, interfere with the operation of any domain in the forest, view or manipulate data stored anywhere in the forest, and view or manipulate data stored on any computer joined to the forest. For this reason, physical access to domain controllers must be restricted to trusted personnel.
- You understand and accept the potential risk that trusted service administrators can be coerced into compromising the security of the system.

Some groups might determine that the collaborative and cost-saving benefits of participating in a shared infrastructure outweigh the risks that service administrators will misuse or will be coerced into misusing their authority. These groups can share a forest and use OUs to delegate authority. However, other groups might not accept this risk because the consequences of a compromise in security are too severe. These groups require separate forests.