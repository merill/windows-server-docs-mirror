---
layout: Conceptual
title: Set Access Scope for a DNS Zone | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/set-access-scope-for-a-dns-zone
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to set the access scope for a DNS zone by using the IPAM client console.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 3ce752e7-628b-8173-f226-14d918953ca2
document_version_independent_id: a8843a17-f767-631d-ed61-1108945fa461
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Set-Access-Scope-for-a-DNS-Zone.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/set-access-scope-for-a-dns-zone
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Set-Access-Scope-for-a-DNS-Zone.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b14427b6-53f0-cb40-7157-e3233648006d
---

# Set Access Scope for a DNS Zone | Microsoft Learn

You can use this topic to set the access scope for a DNS zone by using the IPAM client console.

Membership in **Administrators**, or equivalent, is the minimum required to perform this procedure.

### To set the access scope for a DNS zone

1. In Server Manager, click **IPAM**. The IPAM client console appears.
2. In the navigation pane, click **DNS Zones**. In the display pane, right-click the DNS zone for which you want to change the access scope., and then click **Set Access Scope**.

    ![Set Access Scope](../../media/set-access-scope-for-a-dns-zone/ipam_setaccessscopeofzone_02.jpg)
3. The **Set Access Scope** dialog box opens. If required for your deployment, click to deselect **Inherit access scope from parent**. In **Select the access scope**, select an item, and then click **OK**.

    ![Select the access scope](../../media/set-access-scope-for-a-dns-zone/ipam_setaccessscopeofzone_03.jpg)
4. In the IPAM client console display pane, verify that the access scope for the zone is changed.

    ![Verify that the access scope for the zone is changed](../../media/set-access-scope-for-a-dns-zone/ipam_setaccessscopeofzone_04.jpg)