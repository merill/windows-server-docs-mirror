---
layout: Conceptual
title: Filter the View of DNS Resource Records | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/filter-the-view-of-dns-resource-records
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to filter the view of DNS resource records in the IPAM client console.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 16ac2e31-a4e1-256c-233b-dd8ca649ccdd
document_version_independent_id: c4829333-9fd3-51fe-34b0-11fa8fa48e01
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Filter-the-View-of-DNS-Resource-Records.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/filter-the-view-of-dns-resource-records
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Filter-the-View-of-DNS-Resource-Records.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 623d1f03-140f-6711-7d94-c925f3059be1
---

# Filter the View of DNS Resource Records | Microsoft Learn

You can use this topic to filter the view of DNS resource records in the IPAM client console.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

### To filter the view of DNS resource records

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, in **MONITOR AND MANAGE**, click **DNS Zones**. The navigation pane divides into an upper navigation pane and a lower navigation pane.
3. In the lower navigation pane, click **Forward Lookup**. All IPAM-managed DNS Forward Lookup zones are displayed in the display pane search results.
4. Click on the zone whose records you want to view and filter.
5. In the display pane, click **Current view**, and then click **Resource Records**. The resource records for the zone are shown in the display pane.
6. In the display pane, click **Add criteria**.

    ![Add criteria](../../media/filter-the-view-of-dns-resource-records/ipam_filterrr_01.jpg)
7. Select a criteria from the drop-down list. For example, if you want to view a specific record type, click **Record Type**.

    ![Select a criteria](../../media/filter-the-view-of-dns-resource-records/ipam_filterrr_02.jpg)
8. Click **Add**.

    ![Add the criteria](../../media/filter-the-view-of-dns-resource-records/ipam_filterrr_03.jpg)
9. **Record Type** is added as a search parameter. Enter text for the type of record that you want to find. For example, if you want to view only SRV records, type **SRV**.

    ![Specify the type of record that you want to find](../../media/filter-the-view-of-dns-resource-records/ipam_filterrr_04.jpg)
10. Press ENTER. The DNS resource records are filtered according to the criteria and search phrase that you specified.

    ![Run the filter](../../media/filter-the-view-of-dns-resource-records/ipam_filterrr_05.jpg)