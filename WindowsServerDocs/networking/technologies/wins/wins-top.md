---
layout: Conceptual
title: Windows Internet Name Service (WINS) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/wins/wins-top
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Microsoft plans to remove Windows Internet Name Service (WINS) in Windows Server 2028, though plans can change. Learn how to replace WINS with Domain Name System (DNS).
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ai-usage: ai-assisted
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: e4209745-b88d-8051-0b87-b460c424360c
document_version_independent_id: e4976fc2-b7bf-1a1c-aece-712b7bda5cc9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/wins/wins-top.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/wins/wins-top
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/wins/wins-top.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
platformId: e6b9ccce-2fe6-f92c-b311-1435935410a5
---

# Windows Internet Name Service (WINS) | Microsoft Learn

Windows Internet Name Service (WINS) is a legacy service that maps Network Basic Input/Output System (NetBIOS) computer names to Internet Protocol (IP) addresses. Microsoft plans to remove WINS. If your organization still uses it, plan a transition.

This article explains WINS availability and removal plans and provides guidance for migrating name resolution to Domain Name System (DNS).

## WINS availability in Windows Server 2025 and planned removal in Windows Server 2028

WINS is available in Windows Server 2025, the final Long-Term Servicing Channel (LTSC) release to include and support it. Microsoft continues to support WINS as part of Windows Server 2025 throughout the [Windows Server 2025 lifecycle](/en-us/lifecycle/products/windows-server-2025).

WINS has been removed in Windows Server 2028 Preview. To learn more, see the [Windows Server 2028 Preview removal notice](../../../get-started/removed-deprecated-features-windows-server?tabs=ws28-preview#features-removed). For removal details, see [WINS removal: Moving forward with modern name resolution](https://support.microsoft.com/servicing/os/windows/docs/2025/11/wins-removal-moving-forward-with-modern-name-resolution).

If your network doesn't already have a WINS deployment, don't deploy WINS. Instead, deploy Domain Name System (DNS). DNS also provides computer name registration and resolution services, and includes many additional benefits over WINS, such as integration with Active Directory Domain Services.

For more information, see [Domain Name System (DNS)](../../dns/dns-top)

If your network already has a WINS deployment, we recommend deploying DNS and then decommissioning WINS.