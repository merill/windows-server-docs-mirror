---
layout: Conceptual
title: Role-based Access Control | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/role-based-access-control
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to use role-based access control in IPAM.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: b3282d17-9d7d-8331-f152-17f434401615
document_version_independent_id: 24cbe036-2d22-9009-7cbc-7dd32478422b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Role-based-Access-Control.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/role-based-access-control
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Role-based-Access-Control.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a7275e98-1853-b3f2-f384-1b09462d5ad4
---

# Role-based Access Control | Microsoft Learn

This topic provides information about using role-based access control in IPAM.

Note

In addition to this topic, the following IPAM access control documentation is available in this section.

- [Manage Role Based Access Control with Server Manager](manage-role-based-access-control-with-server-manager)
- [Manage Role Based Access Control with Windows PowerShell](manage-role-based-access-control-with-windows-powershell)

Role-based access control allows you to specify access privileges at various levels, including the DNS server, DNS zone, and DNS resource record levels. By using role based access control, you can specify who has granular control over operations to create, edit, and delete different types of DNS resource records.

You can configure access control so that users are restricted to the following permissions.

- Users can edit only specific DNS resource records
- Users can edit DNS resource records of a specific type, such as PTR or MX
- Users can edit DNS resource records for specific zones