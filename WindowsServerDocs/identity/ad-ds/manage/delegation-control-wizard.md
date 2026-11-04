---
layout: Conceptual
title: Delegation of Control in AD DS on Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/delegation-control-wizard
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn how to delegate administrative control in Active Directory Domain Services on Windows Server.
ms.author: orthomas
author: Orin-Thomas
ms.date: 2025-07-09T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 852d0c32-4622-848d-b397-8b4d874c96ca
document_version_independent_id: 852d0c32-4622-848d-b397-8b4d874c96ca
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/delegation-control-wizard.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/delegation-control-wizard
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/delegation-control-wizard.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: b96755fc-a96f-87ca-7edc-f8f53b0b9436
---

# Delegation of Control in AD DS on Windows Server | Microsoft Learn

Delegation of control means you can assign a range of administrative tasks to different users and groups. You can assign basic administrative tasks to regular users or groups, and leave domain-wide and forest-wide administration to members of the Domain Admins and Enterprise Admins groups. By delegating administration, you can allow groups within your organization to take more control of their local resources. You also help secure your Active Directory environment against accidental or malicious damage by limiting the membership of administrator groups.

You can delegate administrative control to any level of a domain tree by creating organizational units within a domain and delegating administrative control for specific organizational units to particular users or groups. To decide what organizational units you want to create, and which organizational units should contain accounts or shared resources, consider the structure of your organization.

Active Directory defines specific permissions and user rights that can be used for delegating or restricting administrative control. By using a combination of organizational units, groups, and permissions, you can define the most appropriate administrative scope for a particular person. This scope could be an entire domain, all organizational units within a domain, or a single organizational unit.

You can assign administrative control to a user or group by using the *Delegation of Control Wizard*. You can use the Delegation of Control Wizard to delegate the following tasks:

- Create, delete, and manage user accounts
- Reset user passwords and force password change at next logon
- Read all user information
- Modify the membership of a group
- Join a computer to a domain
- Manage Group Policy links
- Generate Resultant Set of Policy (Planning)
- Generate Resultant Set of Policy (Logging)
- Create, delete, and manage inetOrgPerson accounts
- Reset inetOrgPerson passwords and force password change at next sign-in
- Read all inetOrgPerson information

## Prerequisites

Before you can delegate control, you need to meet the following prerequisites.

- You must be a member of the Domain Admins group or have been delegated the necessary permissions to perform the tasks you want to delegate.
- On the computer where you'll delegate control, you must have the AD DS Remote Server Administration Tools (RSAT) installed.

## Delegate control

When you use the Delegation of Control Wizard, you delegate not only at the domain or organizational unit level, but to all objects under the parent container.

To use the Delegation of Control Wizard, perform the following steps:

1. In Active Directory Users and Computers, select the parent container. For example, select the domain or organizational unit over which you want to delegate control.
2. On the **Action** menu, select **Delegate control**. This action starts the Delegation of Control Wizard.
3. On the Users or Groups page, select the users or groups to which you're delegating privileges.
4. On the Tasks to Delegate page, select the task that you want to delegate from a list of common tasks, as described earlier in this article.
5. Select **Finish** to complete the delegation process.

You can also choose the create a custom task to delegate option if you want to create a custom task. Creating a custom task involves specifying the type of object that the task relates to and the permissions you want to delegate. The common tasks apply to all objects within the scope of the container on which you perform delegation.