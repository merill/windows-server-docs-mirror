---
layout: Conceptual
title: Set Access Scope for DNS Resource Records | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/set-access-scope-for-dns-resource-records
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to set the access scope for a DNS resource records by using the IPAM client console.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 5b485e47-23e8-0ff1-7d1e-a56a10385575
document_version_independent_id: 0b9b53de-b112-e09f-88ae-a9544d9381b5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Set-Access-Scope-for-DNS-Resource-Records.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/set-access-scope-for-dns-resource-records
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Set-Access-Scope-for-DNS-Resource-Records.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 6c572fa5-c276-eb1a-91b7-4d0c1b388332
---

# Set Access Scope for DNS Resource Records | Microsoft Learn

You can use this topic to set the access scope for a DNS resource records by using the IPAM client console.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

### To set access scope for DNS resource records

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, click **DNS Zones**. In the lower navigation pane, expand **Forward Lookup** and browse to and select the zone that contains the resource records whose access scope you want to change.
3. In the display pane, locate and select the resource records whose access scope you want to change.

    ![Select the resource records](../../media/set-access-scope-for-dns-resource-records/ipam_restrictusertorrcontrol_02.jpg)
4. Right-click the selected DNS resource records, and then click **Set Access Scope**.

    ![Set Access Scope](../../media/set-access-scope-for-dns-resource-records/ipam_restrictusertorrcontrol_03.jpg)
5. The **Set Access Scope** dialog box opens. If required for your deployment, click to deselect **Inherit access scope from parent**. In **Select the access scope**, select an item, and then click **OK**.

    ![Select the access scope](../../media/set-access-scope-for-dns-resource-records/ipam_restrictusertorrcontrol_04.jpg)