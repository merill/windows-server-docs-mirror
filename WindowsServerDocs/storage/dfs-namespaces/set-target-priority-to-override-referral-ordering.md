---
layout: Conceptual
title: Set Target Priority to Override Referral Ordering | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/set-target-priority-to-override-referral-ordering
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to set the target priority to override referral ordering
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 2d1ae13a-6769-851a-96e6-78ccc007ef33
document_version_independent_id: 6d9db9de-c69f-b417-5012-ae068bdabb62
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/set-target-priority-to-override-referral-ordering.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/set-target-priority-to-override-referral-ordering
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/set-target-priority-to-override-referral-ordering.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 7a80dd12-62f8-f816-89af-4ef9dac0f153
---

# Set Target Priority to Override Referral Ordering | Microsoft Learn

A referral is an ordered list of targets that a client computer receives from a domain controller or namespace server when the user accesses a namespace root or folder with targets in the namespace. Each target in a referral is ordered according to the ordering method for the namespace root or folder.

To refine how targets are ordered, you can set priority on individual targets. For example, you can specify that the target is first among all targets, last among all targets, or first or last among all targets of equal cost.

## To set target priority on a root target for a domain-based namespace

To set target priority on a root target for a domain-based namespace, use the following procedure:

1. Click **Start**, point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, click the domain-based namespace for the root targets for which you want to set priority.
3. In the **Details** pane, on the **Namespace Servers** tab, right-click the root target with the priority that you want to change, and then click **Properties**.
4. On the **Advanced** tab, click **Override referral ordering**, and then click the priority you want.

    - **First among all targets** Specifies that users should always be referred to this target if the target is available.
    - **Last among all targets** Specifies that users should never be referred to this target unless all other targets are unavailable.
    - **First among targets of equal cost** Specifies that users should be referred to this target before other targets of equal cost (which usually means other targets in the same site).
    - **Last among targets of equal cost** Specifies that users should never be referred to this target if there are other targets of equal cost available (which usually means other targets in the same site).

## To set target priority on a folder target

To set target priority on a folder target, use the following procedure:

1. Click **Start**, point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, click the folder of the targets for which you want to set priority.
3. In the **Details** pane, on the **Folder Targets** tab, right-click the folder target with the priority that you want to change, and then click **Properties** .
4. On the **Advanced** tab, click **Override referral ordering** and then click the priority that you want.

Note

To set target priorities by using Windows PowerShell, use the [Set-DfsnRootTarget](/en-us/powershell/module/dfsr/update-dfsrconfigurationfromad) and [Set-DfsnFolderTarget](/en-us/powershell/module/dfsr/update-dfsrconfigurationfromad) cmdlets with the **ReferralPriorityClass** and **ReferralPriorityRank** parameters. These cmdlets were introduced in Windows Server 2012.

## Additional References

- [Tuning DFS Namespaces](tuning-dfs-namespaces)
- [Delegate Management Permissions for DFS Namespaces](delegate-management-permissions-for-dfs-namespaces)