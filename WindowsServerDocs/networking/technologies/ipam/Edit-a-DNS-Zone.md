---
layout: Conceptual
title: Edit a DNS Zone | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/edit-a-dns-zone
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to edit a DNS zone in the IPAM client console.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 6088be30-8991-d5fb-f2ee-aa3cac2b65fa
document_version_independent_id: 637454e9-95db-29b5-db0e-254fdd9f009b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Edit-a-DNS-Zone.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/edit-a-dns-zone
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Edit-a-DNS-Zone.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: fd88904f-0be8-352b-86b3-aca51a30e827
---

# Edit a DNS Zone | Microsoft Learn

You can use this topic to edit a DNS zone in the IPAM client console.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

### To edit a DNS zone

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, in **MONITOR AND MANAGE**, click **DNS Zones**. The navigation pane divides into an upper navigation pane and a lower navigation pane.
3. In the lower navigation pane, make one of the following selections:

    - Forward Lookup
    - IPv4 Reverse Lookup
    - IPv6 Reverse Lookup
4. For example, select IPv4 Reverse Lookup.

    ![Select a zone type](../../media/edit-a-dns-zone/ipam_editzone_01.jpg)
5. In the display pane, right-click the zone that you want to edit, and then click **Edit DNS Zone**.

    ![Edit DNS Zone](../../media/edit-a-dns-zone/ipam_editzone_02.jpg)
6. The **Edit DNS Zone** dialog box opens with the **General** page selected. If needed, edit the General zone properties: **DNS server**, **Zone category**, and **Zone type**, and then click **Apply** or, if your edits are complete, **OK**.

    ![Edit zone properties and save](../../media/edit-a-dns-zone/ipam_editzone_03a.jpg)
7. In the **Edit DNS Zone** dialog box, click **Advanced**. The **Advanced** zone properties page opens. If needed, edit the properties that you want to change, and then click **Apply** or, if your edits are complete, **OK**.

    ![Edit advanced zone properties](../../media/edit-a-dns-zone/ipam_editzone_04a.jpg)
8. If needed, select the additional zone properties page names (Name Servers, SOA, Zone Transfers), make your edits, and click **Apply** or **OK**. To review all of your zone edits, click **Summary**, and then click **OK**.