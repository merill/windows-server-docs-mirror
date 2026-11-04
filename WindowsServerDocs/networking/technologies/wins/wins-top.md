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
description: This topic provides information about decommissioning WINS and using DNS for name resolution services on your network.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
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
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e6b9ccce-2fe6-f92c-b311-1435935410a5
---

# Windows Internet Name Service (WINS) | Microsoft Learn

Windows Internet Name Service (WINS) is a legacy computer name registration and resolution service that maps computer NetBIOS names to IP addresses.

If you do not already have WINS deployed on your network, do not deploy WINS - instead, deploy Domain Name System (DNS). DNS also provides computer name registration and resolution services, and includes many additional benefits over WINS, such as integration with Active Directory Domain Services.

For more information, see [Domain Name System (DNS)](../../dns/dns-top)

If you have already deployed WINS on your network, it is recommended that you deploy DNS and then decommission WINS.