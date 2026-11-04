---
layout: Conceptual
title: Overview of Active Directory Domain Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/active-directory-domain-services-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn about how Active Directory Domain Services, provides the methods for storing directory data and making this data available to network users and administrators.
ms.topic: overview
ms.author: roharwoo
author: robinharwood
ms.date: 2016-10-12T00:00:00.0000000Z
locale: en-us
document_id: f998e855-f99e-7e35-6c10-71109f0d2dd6
document_version_independent_id: f998e855-f99e-7e35-6c10-71109f0d2dd6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/active-directory-domain-services-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/active-directory-domain-services-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/active-directory-domain-services-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 13d646b7-264a-95da-af5e-129839c5d7f5
---

# Overview of Active Directory Domain Services | Microsoft Learn

A directory is a hierarchical structure that stores information about objects on the network. A directory service, such as Active Directory Domain Services (AD DS), provides the methods for storing directory data and making this data available to network users and administrators. For example, AD DS stores information about user accounts, such as names, passwords, phone numbers, and so on, and enables other authorized users on the same network to access this information.

Active Directory stores information about objects on the network and makes this information easy for administrators and users to find and use. Active Directory uses a structured data store as the basis for a logical, hierarchical organization of directory information.

This data store, also known as the directory, contains information about Active Directory objects. These objects typically include shared resources such as servers, volumes, printers, and the network user and computer accounts. For more information about the Active Directory data store, see [Directory data store](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc736627%28v=ws.10%29).

Security is integrated with Active Directory through logon authentication and access control to objects in the directory. With a single network logon, administrators can manage directory data and organization throughout their network, and authorized network users can access resources anywhere on the network. Policy-based administration eases the management of even the most complex network. For more information about Active Directory security, see Security overview.

Active Directory also includes:

- A set of rules, **the schema**, that defines the classes of objects and attributes contained in the directory, the constraints and limits on instances of these objects, and the format of their names. For more information about the schema, see Schema.
- A **global catalog** that contains information about every object in the directory. This allows users and administrators to find directory information regardless of which domain in the directory actually contains the data. For more information about the global catalog, see The role of the global catalog.
- A **query and index mechanism**, so that objects and their properties can be published and found by network users or applications. For more information about querying the directory, see Finding directory information.
- A **replication service** that distributes directory data across a network. All domain controllers in a domain participate in replication and contain a complete copy of all directory information for their domain. Any change to directory data is replicated to all domain controllers in the domain. For more information about Active Directory replication, see Replication overview.

## Understanding Active Directory

This section provides links to core Active Directory concepts:

- [Active Directory Structure and Storage Technologies](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc759186%28v=ws.10%29)
- [Domains Controller Roles](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc786438%28v=ws.10%29)
- Active Directory Schema
- [Understanding Trusts](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771294%28v=ws.10%29)
- [Active Directory Replication Technologies](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc786438%28v=ws.10%29)
- [Active Directory Search and Publication Technologies](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc775686%28v=ws.10%29)
- Interoperating with DNS and Group Policy
- [Understanding Schema](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc759402%28v=ws.10%29)

For a detailed list of Active Directory concepts, see [Understanding Active Directory](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc781408%28v=ws.10%29).