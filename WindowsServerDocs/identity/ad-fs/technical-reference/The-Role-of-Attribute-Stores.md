---
layout: Conceptual
title: The role of attribute stores in AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/technical-reference/the-role-of-attribute-stores
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: This article describes the role of attribute stores in Active Directory Federation Services (AD FS).
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 02e081eb-4551-c928-907a-70fac9b808b3
document_version_independent_id: d2fb697b-50a5-84c7-bdac-0aa7e584a904
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/technical-reference/The-Role-of-Attribute-Stores.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/technical-reference/the-role-of-attribute-stores
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/technical-reference/The-Role-of-Attribute-Stores.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: db8a9e3e-1284-09c8-f399-b076ae7b7138
---

# The role of attribute stores in AD FS | Microsoft Learn

In Active Directory Federation Services (AD FS), the term *attribute stores* refers to directories or databases that an organization uses to store its user accounts and their attribute values. After it's configured in an identity provider organization, AD FS retrieves these attribute values from the store. It creates claims based on that information so that a web application or service that's hosted in a relying party organization can make the appropriate authorization decisions when a federated user (a user whose account is stored in the identity provider organization) tries to access the application or service.

For more information about how claims are generated, see [The role of claims](the-role-of-claims).

## How attribute stores fit in with your AD FS deployment goals

The location of the user attribute store and the location from which users authenticate determine how you design AD FS to support the user identities. Depending on where the attribute store is located and where users will access the application (in an intranet or on the internet), you might have one of these deployment goals:

- **Give your Active Directory users access to your claims-aware applications and services.** In this scenario, users in your organization access an application or service secured by AD FS when the users are signed in to Active Directory in the corporate intranet. The application or service can be your own or a partner's.
- **Give your Active Directory users access to the applications and services of other organizations.** In this scenario, users in your organization access an application or service secured by AD FS when the users are signed in to an attribute store in the corporate intranet and when they sign in remotely from the internet. The application or service can be your own or a partner's.
- **Give users in another organization access to your claims-aware applications and services.** In this scenario, user accounts in another organization that are located in an attribute store on that organization's corporate intranet must access an application secured by AD FS in your organization. This scenario also works when you need to give consumer-based user accounts that are located in an attribute store in your organization's perimeter network access to an application secured by AD FS in your organization.

Depending on attribute store placement and other requirements of your organization, you can combine several of these deployment goals to complete the design of your AD FS deployment.

## Attribute stores that AD FS supports

AD FS supports a wide range of directory and database stores. You can use them to extract administrator-defined attribute values and populate claims with those values. AD FS supports any of these directories or databases as attribute stores:

- Microsoft Entra Domain Services in Windows Server 2012 and 2012 R2, and in Windows Server 2016 and later
- All editions of SQL Server 2012, SQL Server 2014, and SQL Server 2016 and later
- Custom attribute stores