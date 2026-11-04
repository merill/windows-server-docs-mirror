---
layout: Conceptual
title: Planning Forest Root Domain Controller Placement | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/planning-forest-root-domain-controller-placement
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Planning Forest Root Domain Controller Placement'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 3798bba8-e2cc-26eb-ad87-16b8792c6e97
document_version_independent_id: 61497765-53d9-8e9a-8f97-7eeacb1874ab
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Planning-Forest-Root-Domain-Controller-Placement.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/planning-forest-root-domain-controller-placement
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Planning-Forest-Root-Domain-Controller-Placement.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 48c9bb84-1b15-69c4-87b6-ede18385c426
---

# Planning Forest Root Domain Controller Placement | Microsoft Learn

Forest root domain controllers are needed to create trust paths for clients that need to access resources in domains other than their own. Place forest root domain controllers in hub locations and at locations that host datacenters. If users in a given location need to access resources from other domains in the same location, and the network availability between the datacenter and the user location is unreliable, you can either add a forest root domain controller in the location or create a shortcut trust between the two domains. It is more cost efficient to create a shortcut trust between the domains unless you have other reasons to place a forest root domain controller in that location.

Shortcut trusts help to optimize authentication requests made from users located in either domain. For more information about shortcut trusts between domains, see the article [Understanding When to Create a Shortcut Trust](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc754538%28v=ws.11%29).

For a worksheet to assist you in documenting your forest root domain controller placement, see [Job Aids for Windows Server 2003 Deployment Kit](https://microsoft.com/download/details.aspx?id=9608), download Job\_Aids\_Designing\_and\_Deploying\_Directory\_and\_Security\_Services.zip, and open "Domain Controller Placement" (DSSTOPO\_4.doc).

You will need to refer to this information when you create the forest root domain. For more information about deploying the forest root domain, see [Deploying a Windows Server 2008 Forest Root Domain](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731174%28v=ws.10%29).