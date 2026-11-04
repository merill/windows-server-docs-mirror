---
layout: Conceptual
title: View DNS Resource Records for a Specific IP Address | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/view-dns-resource-records-for-a-specific-ip-address
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to view the DNS resource records that are associated with the IP Address that you choose.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: c1afbc14-c683-36ee-2637-a77cded49e90
document_version_independent_id: e0ea22b6-e432-5a77-ca55-3aa4ab761759
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/View-DNS-Resource-Records-for-a-Specific-IP-Address.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/view-dns-resource-records-for-a-specific-ip-address
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/View-DNS-Resource-Records-for-a-Specific-IP-Address.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: bce6562a-b86e-6151-f0bc-9faa18b67992
---

# View DNS Resource Records for a Specific IP Address | Microsoft Learn

You can use this topic to view the DNS resource records that are associated with the IP Address that you choose.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

### To view resource records for an IP Address

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, in **IP ADDRESS SPACE**, click **IP Address Inventory**. In the lower navigation pane, click either **IPv4** or **IPv6**. The IP address inventory appears in the display pane search view. Locate and select the IP address whose DNS resource records you want to view.

    ![View IP address inventory](../../media/view-dns-resource-records-for-a-specific-ip-address/ipam_ipinventory_01.jpg)
3. In the display pane **Details View**, click **DNS resource records**. The resource records that are associated with the selected IP address are displayed.

    ![View DNS resource records](../../media/view-dns-resource-records-for-a-specific-ip-address/ipam_ipinventory_02.jpg)