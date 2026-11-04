---
layout: Conceptual
title: DNS and AD DS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/dns-and-ad-ds
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: DNS and AD DS'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 456f3044-dda3-9e08-343c-c7c059264be4
document_version_independent_id: 9a4a5cfd-0341-03d1-7278-cdc87141a1bd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/DNS-and-AD-DS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/dns-and-ad-ds
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/DNS-and-AD-DS.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 8c864245-6aa6-fce5-6797-fe88924eb490
---

# DNS and AD DS | Microsoft Learn

Active Directory Domain Services (AD DS) uses Domain Name System (DNS) name resolution services to make it possible for clients to locate domain controllers and for the domain controllers that host the directory service to communicate with each other.

AD DS enables easy integration of the Active Directory namespace into an existing DNS namespace. Features such as Active Directory-integrated DNS zones make it easier for you to deploy DNS by eliminating the need to set up secondary zones, and then configure zone transfers.

For information about how DNS supports AD DS, see the section [DNS Support for Active Directory Technical Reference](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc781627%28v=ws.10%29).

Note

If you implement a disjoint namespace in which the AD DS domain name differs from the primary DNS suffix that clients use, AD DS integration with DNS is more complex. For more information, see [Disjoint Namespace](disjoint-namespace).