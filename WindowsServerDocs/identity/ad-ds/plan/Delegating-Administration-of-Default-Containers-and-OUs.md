---
layout: Conceptual
title: Delegating Administration of Default Containers and OUs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/delegating-administration-of-default-containers-and-ous
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Delegating Administration of Default Containers and OUs'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 11564f93-cb40-c76e-4426-de5f103e83ca
document_version_independent_id: 6ed87766-f20b-d93c-0ed5-6784a4061f59
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Delegating-Administration-of-Default-Containers-and-OUs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/delegating-administration-of-default-containers-and-ous
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Delegating-Administration-of-Default-Containers-and-OUs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b6406131-d099-95b1-1278-e09581ce79c4
---

# Delegating Administration of Default Containers and OUs | Microsoft Learn

Every Active Directory domain contains a standard set of containers and organizational units (OUs) that are created during the installation of Active Directory Domain Services (AD DS). These include the following:

- Domain container, which serves as the root container to the hierarchy
- Built-in container, which holds the default service administrator accounts
- Users container, which is the default location for new user accounts and groups created in the domain
- Computers container, which is the default location for new computer accounts created in the domain
- Domain Controllers OU, which is the default location for the computer accounts for domain controllers computer accounts

The forest owner controls these default containers and OUs.

## Domain container

The domain container is the root container of the hierarchy of a domain. Changes to the policies or the access control list (ACL) on this container can potentially have domain-wide impact. Do not delegate control of this container; it must be controlled by the service administrators.

## Users and computers containers

When you perform an in-place domain upgrade from Windows Server 2003 to Windows Server 2008 , existing users and computers are automatically placed into the users and the computers containers. If you are creating a new Active Directory domain, the users and computers containers are the default locations for all new user accounts and non-domain-controller computer accounts in the domain.

Important

If you need to delegate control over users or computers, do not modify the default settings on the users and computers containers. Instead, create new OUs (as needed) and move the user and computer objects from their default containers and into the new OUs. Delegate control over the new OUs, as needed. We recommend that you not modify who controls the default containers.

Also, you cannot apply Group Policy settings to the default users and computers containers. To apply Group Policy to users and computers, create new OUs and move the user and computer objects into those OUs. Apply the Group Policy settings to the new OUs.

Optionally, you can redirect the creation of objects that are placed in the default containers to be placed in containers of your choice.

## Well-known users and groups and built-in accounts

By default, several well-known users and groups and built-in accounts are created in a new domain. We recommend that management of these accounts remains under the control of the service administrators. Do not delegate management of these accounts to an individual who is not a service administrator. The following table lists the well-known users and groups and built-in accounts that need to remain under the control of the service administrators.

| Well-known users and groups | Built-in accounts |
| --- | --- |
| Cert Publishers<br>Domain Controllers<br><br>Group Policy Creator Owners<br><br>KRBTGT<br><br>Domain Guests<br><br>Administrator<br><br>Domain Admins<br><br>Schema Admins (forest root domain only)<br><br>Enterprise Admins (forest root domain only)<br><br>Domain Users | Administrator<br>Guest<br><br>Guests<br><br>Account Operators<br><br>Administrators<br><br>Backup Operators<br><br>Incoming Forest Trust Builders<br><br>Print Operators<br><br>Pre-Windows 2000 Compatible Access<br><br>Server Operators<br><br>Users |

## Domain Controller OU

When domain controllers are added to the domain, their computer objects are automatically added to the Domain Controller OU. This OU has a default set of policies applied to it. To ensure that these policies are applied uniformly to all domain controllers, we recommend that you not move the computer objects of the domain controllers out of this OU. Failure to apply the default policies can cause a domain controller to fail to function properly.

By default, the service administrators control this OU. Do not delegate control of this OU to individuals other than the service administrators.