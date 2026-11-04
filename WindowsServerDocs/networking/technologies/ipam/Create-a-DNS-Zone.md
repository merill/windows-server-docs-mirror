---
layout: Conceptual
title: Create a DNS Zone | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/create-a-dns-zone
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to create a DNS zone by using the IPAM client console.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 61a35562-ca72-aff9-545d-2ce371384310
document_version_independent_id: cbc6e821-c5db-6950-0a8a-123de8085a78
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Create-a-DNS-Zone.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/create-a-dns-zone
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Create-a-DNS-Zone.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 76167337-06b5-0d38-c876-749fc2bde80c
---

# Create a DNS Zone | Microsoft Learn

You can use this topic to create a DNS zone by using the IPAM client console.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

### To create a DNS zone

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, in **MONITOR AND MANAGE**, click **DNS and DHCP Servers**. In the display pane, click **Server Type**, and then click **DNS**. All DNS servers that are managed by IPAM are listed in the search results.
3. Locate the server where you want to add a zone, and right-click the server. Click **Create DNS zone**.

    ![Create DNS zone](../../media/create-a-dns-zone/ipam_creatednszone_01a.jpg)
4. The **Create DNS Zone** dialog box opens. In **General Properties**, select a zone category, a zone type , and enter a name in **Zone name**. Also select values appropriate for your deployment in **Advanced Properties**, and then click **OK**.

    ![Advanced Properties](../../media/create-a-dns-zone/ipam_creatednszone_02a.jpg)