---
layout: Conceptual
title: Delete DNS Resource Records | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/delete-dns-resource-records
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to delete one or more DNS resource records by using the IPAM client console.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 712adb25-6c93-4f19-f85f-932edf8dd1f3
document_version_independent_id: 383da9b0-bfd2-5f70-58cc-45058351ad30
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Delete-DNS-Resource-Records.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/delete-dns-resource-records
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Delete-DNS-Resource-Records.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 2e8abd09-43e1-246a-811c-a30c2e651a6b
---

# Delete DNS Resource Records | Microsoft Learn

You can use this topic to delete one or more DNS resource records by using the IPAM client console.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

## To delete DNS resource records

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, in **MONITOR AND MANAGE**, click **DNS Zones**. The navigation pane divides into an upper navigation pane and a lower navigation pane.
3. Click to expand **Forward Lookup** and the domain where the zone and resource records that you want to delete are located. Click on the zone, and in the display pane, click **Current view**. Click **Resource Records**.
4. In the display pane, locate and select the resource records that you want to delete.

    ![Screenshot showing how to select resource records to delete.](../../media/delete-dns-resource-records/ipam_deleterr_01.jpg)
5. Right-click the selected records, and then click **Delete DNS resource record**.

    ![Screenshot showing how to delete the records.](../../media/delete-dns-resource-records/ipam_deleterr_02.jpg)
6. The **Delete DNS Resource Record** dialog box opens. Verify that the correct DNS server is selected. If it isn't, click **DNS server** and select the server from which you want to delete the resource records. Click **OK**. IPAM deletes the resource records from the DNS server.

    ![Screenshot showing how to verify that the correct DNS server is selected and delete the records.](../../media/delete-dns-resource-records/ipam_deleterr_03.jpg)