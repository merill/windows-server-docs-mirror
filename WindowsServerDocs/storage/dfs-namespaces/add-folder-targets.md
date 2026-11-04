---
layout: Conceptual
title: Add folder targets in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/add-folder-targets
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to add folder targets (UNC paths) in the Windows Server environment.
ms.author: roharwoo
ms.topic: how-to
author: robinharwood
ms.date: 2023-05-11T00:00:00.0000000Z
locale: en-us
document_id: 2ec4a34c-e5f5-9dd1-f9de-85ac5d6cf0fe
document_version_independent_id: aa11ddeb-5179-5440-caaa-76d7af8a4a36
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/add-folder-targets.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/add-folder-targets
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/add-folder-targets.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: c0437728-c4d0-dbb1-2d33-07bc8dde889a
---

# Add folder targets in Windows Server | Microsoft Learn

A folder target is the Universal Naming Convention (UNC) path of a shared folder or another namespace that is associated with a folder in a namespace. Adding multiple folder targets increases the availability of the folder in the namespace.

## Prerequisites

The following must be installed to use this feature:

- A Windows Server with the **DFS Namespaces** role service installed as part of the **File and Storage Services** server role. To learn more, see [Install or Uninstall Roles, Role Services, or Features](/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features).
- An account with Administrative privileges.
- A server to host the DFS folder target.

## Add a folder target

To add a folder target by using DFS Management, perform the following:

1. Click **Start** &gt; **Windows Administrative Tools** &gt; select **DFS Management**. *Alternatively, click **Start** &gt; type **dfsmgmt.msc** &gt; hit*Enter.
2. In the console tree, under the **Namespaces** node, right-click on the namespace where you want to add the folder, then select **New Folder**.
3. In the popup box, provide a name for this folder in the **Name** field, then click **Add**.
4. Type the path to the folder target, or click **Browse** to locate the folder target, click **OK**, then click **OK** again.

The following animation demonstrates the steps to add a folder target by using DFS Management.

![A video demonstrating how to add a target folder using DFS management in Windows Server.](media/add-folder-targets-gif.gif)

If the folder is replicated using DFS Replication, you can specify whether to add the new folder target to the replication group.

Tip

To add a folder target by using Windows PowerShell, use the [New-DfsnFolderTarget](/en-us/powershell/module/dfsn/new-dfsnfoldertarget) cmdlet. The DFSN Windows PowerShell module was introduced in Windows Server 2012.

Note

Folders can contain folder targets or other DFS folders, but not both, at the same level in the folder hierarchy.

## Additional references

- [Deploying DFS Namespaces](deploying-dfs-namespaces)
- [Delegate Management Permissions for DFS Namespaces](delegate-management-permissions-for-dfs-namespaces)
- [Replicate Folder Targets Using DFS Replication](replicate-folder-targets-using-dfs-replication)