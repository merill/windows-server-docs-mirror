---
layout: Conceptual
title: Change the Amount of Time that Clients Cache Referrals | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/change-the-amount-of-time-that-clients-cache-referrals
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to change the amount of time that clients cache referrals
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 8c625423-1342-fe4c-1e52-dd8728e70878
document_version_independent_id: e8c6df95-7271-2f29-5c94-01e69d72c5d6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/change-the-amount-of-time-that-clients-cache-referrals.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/change-the-amount-of-time-that-clients-cache-referrals
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/change-the-amount-of-time-that-clients-cache-referrals.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 974c6d90-531c-76ca-5a00-5ab996734523
---

# Change the Amount of Time that Clients Cache Referrals | Microsoft Learn

A referral is an ordered list of targets that a client computer receives from a domain controller or namespace server when the user accesses a namespace root or folder with targets in the namespace. You can adjust how long clients cache a referral before requesting a new one.

## To change the amount of time that clients cache namespace root referrals

1. Click **Start**, point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, right-click a namespace, and then click **Properties**.
3. On the **Referrals** tab, in the **Cache duration (in seconds)** text box, type the amount of time (in seconds) that clients cache namespace root referrals. The default setting is 300 seconds (five minutes).

Tip

To change the amount of time that clients cache namespace root referrals by using Windows PowerShell, use the [Set-DfsnRoot TimeToLiveSec](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753448%28v=ws.11%29) cmdlet. These cmdlets were introduced in Windows Server 2012.

## To change the amount of time that clients cache folder referrals

1. Click **Start** , point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, right-click a folder that has targets, and then click **Properties**.
3. On the **Referrals** tab, in the **Cache duration (in seconds)** text box, type the amount of time (in seconds) that clients cache folder referrals. The default setting is 1800 seconds (30 minutes).

## Additional References

- [Tuning DFS Namespaces](tuning-dfs-namespaces)
- [Delegate Management Permissions for DFS Namespaces](delegate-management-permissions-for-dfs-namespaces)