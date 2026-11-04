---
layout: Conceptual
title: Active Directory Domain Services overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Find out about Active Directory Domain Services, a directory service that makes network resource data available to authorized network users and administrators.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-03-10T00:00:00.0000000Z
ms.topic: overview
locale: en-us
document_id: b0303f4b-d7bd-e5e6-f168-92b9bed38c58
document_version_independent_id: aade2fb6-db2e-c3d6-723e-77fdffdf6781
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/get-started/virtual-dc/Active-Directory-Domain-Services-Overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/get-started/virtual-dc/Active-Directory-Domain-Services-Overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: b3588e2f-8990-8d4f-1d5a-9e06bbb14373
---

# Active Directory Domain Services overview | Microsoft Learn

A directory is a hierarchical structure that stores information about objects on a network. A directory service, such as Active Directory Domain Services (AD DS), provides the methods for storing directory data and making this data available to network users and administrators. For example, AD DS stores information about user accounts, such as names, passwords, phone numbers, and so on. AD DS also provides a way for authorized users on the same network to access this information.

AD DS stores information about objects on the network and makes this information easy for administrators and users to find and use. AD DS uses a structured data store as the basis for a logical, hierarchical organization of directory information.

This data store, also known as the directory, contains information about AD DS objects. These objects typically include shared resources such as servers, volumes, printers, and the network user and computer accounts. For more information about the AD DS data store, see [Directory data store](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc736627%28v=ws.10%29).

Security is integrated with AD DS through sign-in authentication and access control to objects in the directory. With a single network username and password, administrators can manage directory data and organization throughout their network, and authorized network users can access resources anywhere on the network. Policy-based administration eases the management of even the most complex network. For more information about AD DS security, see [Best practices for securing Active Directory](../../plan/security-best-practices/best-practices-for-securing-active-directory).

AD DS also includes:

- A set of rules, the **schema**, that defines the classes of objects and attributes contained in the directory, the constraints and limits on instances of these objects, and the format of their names. For more information about the schema, see [Schema](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc756876%28v=ws.10%29).
- A **global catalog** that contains information about every object in the directory. Users and administrators can use the catalog to find directory information regardless of the directory domain that actually contains the data. For more information about the global catalog, see [Global catalog](/en-us/windows/win32/ad/global-catalog).
- A **query and index mechanism**, so that objects and their properties can be published and found by network users or applications. For more information about querying the directory, see [Searching in Active Directory Domain Services](/en-us/windows/win32/ad/searching-in-active-directory-domain-services).
- A **replication service** that distributes directory data across a network. All domain controllers in a domain participate in replication and contain a complete copy of all directory information for their domain. Any change to directory data is replicated to all domain controllers in the domain. For more information about AD DS replication, see [Active Directory Replication Concepts](../replication/active-directory-replication-concepts).

## Understand AD DS

This section provides links to core AD DS concepts:

- [Active Directory Structure and Storage Technologies](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc759186%28v=ws.10%29)
- [Domain Controller Roles](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc786438%28v=ws.10%29)
- [Active Directory Schema](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc771796%28v=ws.10%29)
- [Managing Trusts](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc771568%28v=ws.10%29)
- [Active Directory Replication Technologies](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc776877%28v=ws.10%29)
- [Active Directory Search and Publication Technologies](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc775686%28v=ws.10%29)
- [DNS Group Policy Settings](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd197486%28v=ws.10%29)
- [Active Directory Schema Technical Reference](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc759402%28v=ws.10%29)

For a detailed list of AD DS concepts, see [Understanding Active Directory](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc781408%28v=ws.10%29).