---
layout: Conceptual
title: View DNS Resource Records for a DNS Zone | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/view-dns-resource-records-for-a-dns-zone
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to view DNS resource records for a DNS zone in the IPAM client console.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 8e594157-e50c-67a2-edda-2f48e788f006
document_version_independent_id: 02c0500d-bd72-c88a-d57c-e0f0d07d8292
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/View-DNS-Resource-Records-for-a-DNS-Zone.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/view-dns-resource-records-for-a-dns-zone
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/View-DNS-Resource-Records-for-a-DNS-Zone.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: eb8de461-659d-0d2a-4186-3015f2d7e3ae
---

# View DNS Resource Records for a DNS Zone | Microsoft Learn

You can use this topic to view DNS resource records for a DNS zone in the IPAM client console.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

### To view DNS resource records for a zone

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, in **MONITOR AND MANAGE**, click **DNS Zones**. The navigation pane divides into an upper navigation pane and a lower navigation pane.
3. In the lower navigation pane, click **Forward Lookup**, and then expand the domain and zone list to locate and select the zone you want to view. For example, if you have a zone named dublin, click **dublin**.

    ![Select the zone you want to view](../../media/view-dns-resource-records-for-a-dns-zone/ipam_dnszones_01a.jpg)
4. In the display pane, the default view is of the DNS servers for the zone. To change the view, click **Current view**, and then click **Resource Records**.

    ![Change the view to Resource Records](../../media/view-dns-resource-records-for-a-dns-zone/ipam_zone_rr_02.jpg)
5. The DNS resource records for the zone are displayed. To filter the records, type the text you want to find in **Filter**.

    ![Type text to filter records](../../media/view-dns-resource-records-for-a-dns-zone/ipam_dnszones_01c.jpg)
6. To filter the resource records by record type, access scope, or other criteria, click **Add criteria**, and then make selections from the criteria list and click **Add**.

    ![Use criteria to filter records](../../media/view-dns-resource-records-for-a-dns-zone/ipam_dnszones_01d.jpg)