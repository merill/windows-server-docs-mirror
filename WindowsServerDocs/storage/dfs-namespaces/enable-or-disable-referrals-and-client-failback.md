---
layout: Conceptual
title: Enable or Disable Referrals and Client Failback | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/enable-or-disable-referrals-and-client-failback
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to enable or disable referrals and client failback.
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: f4505ffb-86d8-2f30-4ff9-582d89486338
document_version_independent_id: 623548d7-e92e-645e-9875-0f53446d8c94
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/enable-or-disable-referrals-and-client-failback.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/enable-or-disable-referrals-and-client-failback
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/enable-or-disable-referrals-and-client-failback.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6e45fa58-2885-1240-71c7-713f7c46edfb
---

# Enable or Disable Referrals and Client Failback | Microsoft Learn

A referral is an ordered list of servers that a client computer receives from a domain controller or namespace server when the user accesses a namespace root or DFS folder with targets. After the computer receives the referral, the computer attempts to access the first server in the list. If the server is not available, the client computer attempts to access the next server. If a server becomes unavailable, you can configure clients to fail back to the preferred server after it becomes available.

The following sections provide information about how to enable or disable referrals or enable client failback:

## Enable or disable referrals

By disabling a namespace server's or folder target's referral, you can prevent users from being directed to that namespace server or folder target. This is useful if you need to temporarily take a server offline for maintenance.

- To enable or disable referrals to a folder target, use the following steps:

    1. In the DFS Management console tree, under the **Namespaces** node, click a folder containing targets, and then click the **Folder Targets** tab in the **Details** pane.
    2. Right-click the folder target, and then click either **Disable Folder Target** or **Enable Folder Target**.
- To enable or disable referrals to a namespace server, use the following steps:

    1. In the DFS Management console tree, select the appropriate namespace and then click the **Namespace Servers** tab.
    2. Right-click the appropriate namespace server and then click either **Disable Namespace Server** or **Enable Namespace Server**.

Tip

To enable or disable referrals by using Windows PowerShell, use the [Set-DfsnRootTarget –State](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731089%28v=ws.11%29) or [Set-DfsnServerConfiguration](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731089%28v=ws.11%29) cmdlets, which were introduced in Windows Server 2012.

## Enable client failback

If a target becomes unavailable, you can configure clients to fail back to the target after it is restored. For failback to work, client computers must meet the requirements listed in the following topic: [Review DFS Namespaces Client Requirements](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771913%28v=ws.11%29).

Note

To enable client failback on a namespace root by using Windows PowerShell, use the [Set-DfsnRoot](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771913%28v=ws.11%29) cmdlet. To enable client failback on a DFS folder, use the [Set-DfsnFolder](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771913%28v=ws.11%29) cmdlet.

## To enable client failback for a namespace root

1. Click **Start**, point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, right-click a namespace, and then click **Properties**.
3. On the **Referrals** tab, select the **Clients fail back to preferred targets** check box.

Folders with targets inherit client failback settings from the namespace root. If client failback is disabled on the namespace root, you can use the following procedure to enable the client to fail back on a folder with targets.

## To enable client failback for a folder with targets

1. Click **Start**, point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, right-click a folder with targets, and then click **Properties**.
3. On the **Referrals** tab, click the **Clients fail back to preferred targets** check box.

## Additional References

- [Tuning DFS Namespaces](tuning-dfs-namespaces)
- [Review DFS Namespaces Client Requirements](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771913%28v=ws.11%29)
- [Delegate Management Permissions for DFS Namespaces](delegate-management-permissions-for-dfs-namespaces)