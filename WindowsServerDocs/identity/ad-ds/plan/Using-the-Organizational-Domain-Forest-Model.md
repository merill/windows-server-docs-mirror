---
layout: Conceptual
title: Using the Organizational Domain Forest Model | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/using-the-organizational-domain-forest-model
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Using the Organizational Domain Forest Model'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 448fe2f9-7e8c-dc74-1455-d0e9d95f851d
document_version_independent_id: 3bb01fe3-573d-90cb-30d8-e768da31e0bd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Using-the-Organizational-Domain-Forest-Model.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/using-the-organizational-domain-forest-model
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Using-the-Organizational-Domain-Forest-Model.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: da38839d-f0d8-feb6-be1f-88d4ff3f76d2
---

# Using the Organizational Domain Forest Model | Microsoft Learn

In the organizational domain forest model, several autonomous groups each own a domain within a forest. Each group controls domain-level service administration, which enables them to manage certain aspects of service management autonomously while the forest owner controls forest-level service management.

The following illustration shows an organizational domain forest model.

![using the org domain forest model](../../media/using-the-organizational-domain-forest-model/c50a3c6a-b0e4-43ec-ad62-f05d05f0bbd2.gif)

## Domain-level service autonomy

The organizational domain forest model enables the delegation of authority for domain-level service management. The following table lists the types of service management that can be controlled at the domain level.

| Type of service management | Associated tasks |
| --- | --- |
| Management of domain controller operations | - Creating and removing domain controllers- Monitoring the functioning of domain controllers- Managing services that are running on domain controllers- Backing up and restoring the directory |
| Configuration of domain-wide settings | - Creating domain and domain user account policies, such as password, Kerberos, and account lockout policies- Creating and applying domain-wide Group Policy |
| Delegation of data-level administration | - Creating organizational units (OUs) and delegating administration- Repairing problems in the OU structure that OU owners do not have sufficient access rights to fix |
| Management of external trusts | - Establishing trust relationships with domains outside the forest |

Other types of service management, such as schema or replication topology management, are the responsibility of the forest owner.

## Domain owner

In an organizational domain forest model, domain owners are responsible for domain-level service management tasks. Domain owners have authority over the entire domain as well as access to all other domains in the forest. For this reason, domain owners must be trusted individuals selected by the forest owner.

Delegate domain-level service management to a domain owner, if the following conditions are met:

- All groups participating in the forest trust the new domain owner and the service management practices of the new domain.
- The new domain owner trusts the forest owner and all the other domain owners.
- All domain owners in the forest agree that the new domain owner has service administrator management and selection policies and practices that are equal to or more strict than their own.
- All domain owners in the forest agree that domain controllers managed by the new domain owner in the new domain are physically secure.

Note that if a forest owner delegates domain-level service management to a domain owner, other groups might choose not to join that forest if they do not trust that domain owner.

All domain owners must be aware that if any of these conditions change in the future, it might become necessary to move the organizational domains into a multiple forest deployment.

Note

Another way to minimize security risks to a Windows Server 2008 Active Directory domain is to employ administrator role separation, which requires the deployment of a read-only domain controller (RODC) in your Active Directory infrastructure. An RODC is a new type of domain controller in the Windows Server 2008 operating system that hosts read-only partitions of the Active Directory database. Before the release of Windows Server 2008 , any server maintenance work on a domain controller had to be performed by a domain administrator. In Windows Server 2008 , you can delegate local administrative permissions for an RODC to any domain user without granting that user any administrative rights for the domain or other domain controllers. This permits the delegated user to log on to an RODC and perform maintenance work, such as upgrading a driver, on the server. However, this delegated user cannot log on to any other domain controller or perform any other administrative task in the domain. In this way, any trusted user can be delegated the ability to effectively manage the RODC without compromising the security of the rest of the domain. For more information about RODCs, see [AD DS: Read-Only Domain Controllers](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc732801%28v=ws.10%29).