---
layout: Conceptual
title: Set the Ordering Method for Targets in Referrals | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/set-the-ordering-method-for-targets-in-referrals
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to set the ordering method for targets in referrals.
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: ad5135ec-8b2b-71d6-7823-e3c3c4569150
document_version_independent_id: a246eef9-b0cd-350a-10e1-0db49368394e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/set-the-ordering-method-for-targets-in-referrals.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/set-the-ordering-method-for-targets-in-referrals
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/set-the-ordering-method-for-targets-in-referrals.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: a68e622f-e540-faf8-1a99-bec011c46ff2
---

# Set the Ordering Method for Targets in Referrals | Microsoft Learn

A referral is an ordered list of targets that a client computer receives from a domain controller or namespace server when the user accesses a namespace root or folder with targets. After the client receives the referral, the client attempts to access the first target in the list. If the target is not available, the client attempts to access the next target. Targets on the client's site are always listed first in a referral. Targets outside of the client's site are listed according to the ordering method.

Use the following sections to specify in what order targets should be referred to clients and to understand the different methods of ordering target referrals:

## To set the ordering method for targets in namespace root referrals

Use the following procedure to set the ordering method on the namespace root:

1. Click **Start**, point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, right-click a namespace, and then click **Properties**.
3. On the **Referrals** tab, select an ordering method.

Note

To use Windows PowerShell to set the ordering method for targets in namespace root referrals, use the [Set-DfsnRoot](/en-us/powershell/module/dfsr/update-dfsrconfigurationfromad) cmdlet with one of the following parameters:

- **EnableSiteCosting** specifies the **Lowest cost ordering** method
- **EnableInsiteReferrals** specifies the **Exclude targets outside of the client's site** ordering method
- Omitting either parameter specifies the **Random order** referral ordering method.

The DFSN Windows PowerShell module was introduced in Windows Server 2012.

## To set the ordering method for targets in folder referrals

Folders with targets inherit the ordering method from the namespace root. You can override the ordering method by using the following procedure:

1. Click **Start**, point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, right-click a folder with targets, and then click **Properties**.
3. On the **Referrals** tab, select the **Exclude targets outside of the client's site** check box.

Note

To use Windows PowerShell to exclude folder targets outside of the client's site, use the [Set-DfsnFolder –EnableInsiteReferrals](/en-us/powershell/module/dfsr/update-dfsrconfigurationfromad) cmdlet.

## Target referral ordering methods

The three ordering methods are:

- Random order
- Lowest cost
- Exclude targets outside of the client's site

## Random order

In this method, targets are ordered as follows:

1. Targets in the same Active Directory Directory Services (AD DS) site as the client are listed in random order at the top of the referral.
2. Targets outside of the client's site are listed in random order.

If no same-site target servers are available, the client computer is referred to a random target server regardless of how expensive the connection is or how distant the target.

## Lowest cost

In this method, targets are ordered as follows:

1. Targets in the same site as the client are listed in random order at the top of the referral.
2. Targets outside of the client's site are listed in order of lowest cost to highest cost. Referrals with the same cost are grouped together, and the targets are listed in random order within each group.

Note

Site link costs are not shown in the DFS Management snap-in. To view site link costs, use the Active Directory Sites and Services snap-in.

## Exclude targets outside of the client's site

In this method, the referral contains only the targets that are in the same site as the client. These same-site targets are listed in random order. If no same-site targets exist, the client does not receive a referral and cannot access that portion of the namespace.

Note

Targets that have target priority set to "First among all targets" or "Last among all targets" are still listed in the referral, even if the ordering method is set to **Exclude targets outside of the client's site**.

## Additional References

- [Tuning DFS Namespaces](tuning-dfs-namespaces)
- [Delegate Management Permissions for DFS Namespaces](delegate-management-permissions-for-dfs-namespaces)