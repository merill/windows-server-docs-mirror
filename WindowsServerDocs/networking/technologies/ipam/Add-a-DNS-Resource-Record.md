---
layout: Conceptual
title: Add a DNS Resource Record | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/add-a-dns-resource-record
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to add one or more new DNS resource records by using the IPAM client console.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2020-08-07T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: d9bcb324-7723-e93a-2258-52bb1e06ae1d
document_version_independent_id: ee86e970-d7c2-f12b-28af-f349fbc7ce0c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Add-a-DNS-Resource-Record.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/add-a-dns-resource-record
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Add-a-DNS-Resource-Record.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: b0e70c5a-5f12-4765-ccdf-409695390627
---

# Add a DNS Resource Record | Microsoft Learn

You can use this topic to add one or more new DNS resource records by using the IPAM client console.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

### To add a DNS resource record

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, in **MONITOR AND MANAGE**, click **DNS Zones**. The navigation pane divides into an upper navigation pane and a lower navigation pane.
3. In the lower navigation pane, click **Forward Lookup**. All IPAM-managed DNS Forward Lookup zones are displayed in the display pane search results. Right-click the zone where you want to add a resource record, and then click **Add DNS resource record**.

    ![Add DNS resource record](../../media/add-a-dns-resource-record/ipam_dnsrr_01.jpg)
4. The **Add DNS Resource Records** dialog box opens. In **Resource record properties**, click **DNS server** and select the DNS server where you want to add one or more new resource records. In **Configure DNS resource records**, click **New**.

    ![Configure DNS resource records](../../media/add-a-dns-resource-record/ipam_dnsrr_02.jpg)
5. The dialog box expands to reveal **New Resource Record**. Click **Resource record type**.

    ![Resource record type](../../media/add-a-dns-resource-record/ipam_dnsrr_03.jpg)
6. The list of resource record types is displayed. Click the resource record type that you want to add.

    ![Select record type to add](../../media/add-a-dns-resource-record/ipam_dnsrr_04.jpg)
7. In **New Resource Record,** in **Name**, type a resource record name. In **IP Address**, type an IP address, and then select the resource record properties that are appropriate for your deployment. Click **Add Resource Record**.

    ![Screenshot of the Resource record page of the Add Resource Record wizard showing the New Resource Record section.](../../media/add-a-dns-resource-record/ipam_dnsrr_06.jpg)
8. If you do not want to create additional new resource records, click **OK**. If you want to create additional new resource records, click **New**.

    ![Click OK or New](../../media/add-a-dns-resource-record/ipam_dnsrr_r2_01.jpg)
9. The dialog box expands to reveal **New Resource Record**. Click **Resource record type**. The list of resource record types is displayed. Click the resource record type that you want to add.
10. In **New Resource Record,** in **Name**, type a resource record name. In **IP Address**, type an IP address, and then select the resource record properties that are appropriate for your deployment. Click **Add Resource Record**.

    ![Screenshot of the Resource record page of the Add Resource Record wizard with the Add Resource Record option highlighted.](../../media/add-a-dns-resource-record/ipam_dnsrr_r2_02.jpg)
11. If you want to add more resource records, repeat the process for creating records. When you are done creating new resource records, click **Apply**.

    ![Complete resource record creation](../../media/add-a-dns-resource-record/ipam_dnsrr_r2_03.jpg)
12. The **Add Resource Record** dialog box displays a resource records summary while IPAM creates the resource records on the DNS server that you specified. When the records are successfully created, the **Status** of the record is **Success**.

    ![Record addition status](../../media/add-a-dns-resource-record/ipam_dnsrr_r2_04.jpg)
13. Click **OK**.