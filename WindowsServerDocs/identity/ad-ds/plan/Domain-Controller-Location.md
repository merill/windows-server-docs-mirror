---
layout: Conceptual
title: Domain Controller Location | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/domain-controller-location
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Domain Controller Location'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: d1f14145-c34e-5b30-d078-5e2f2ad5eea9
document_version_independent_id: f2461ac6-8a43-5153-4976-63365beb8ce3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Domain-Controller-Location.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/domain-controller-location
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Domain-Controller-Location.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 4483b833-74d1-fc77-4c40-28251b5fbb87
---

# Domain Controller Location | Microsoft Learn

Clients use Domain Name System (DNS) to locate domain controllers to complete operations such as processing logon requests or searching the directory for published resources. Domain controllers register a variety of records in DNS to help clients and other computers locate them. These records are collectively referred to as the locator records.

Domain controllers also use DNS to locate other domain controllers and to perform tasks such as replication. The process by which domain controllers locate other domain controllers is the same as the process by which clients locate domain controllers.