---
layout: Conceptual
title: Create a Folder in a DFS Namespace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/create-a-folder-in-a-dfs-namespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to create a folder in a DFS namespace
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: a673699e-7911-fb0f-bb86-27d16449147e
document_version_independent_id: e68208b9-6df2-8be2-1de5-7332e3cb181e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/create-a-folder-in-a-dfs-namespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/create-a-folder-in-a-dfs-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/create-a-folder-in-a-dfs-namespace.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: afbf9e8d-8c64-1ed0-92c7-dbed06fa4cf7
---

# Create a Folder in a DFS Namespace | Microsoft Learn

You can use folders to create additional levels of hierarchy in a namespace. You can also create folders with folder targets to add shared folders to the namespace. DFS folders with folder targets cannot contain other DFS folders, so if you want to add a level of hierarchy to the namespace, do not add folder targets to the folder.

Use the following procedure to create a folder in a namespace using DFS Management:

## To create a folder in a DFS namespace

1. Click **Start**, point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, right-click a namespace or a folder within a namespace, and then click **New Folder**.
3. In the **Name** text box, type the name of the new folder.
4. To add one or more folder targets to the folder, click **Add** and specify the Universal Naming Convention (UNC) path of the folder target, and then click **OK** .

Tip

To create a folder in a namespace by using Windows PowerShell, use the [New-DfsnFolder](/en-us/powershell/module/dfsn/new-dfsnfolder) cmdlet. The DFSN Windows PowerShell module was introduced in Windows Server 2012.

## Additional References

- [Deploying DFS Namespaces](deploying-dfs-namespaces)
- [Delegate Management Permissions for DFS Namespaces](delegate-management-permissions-for-dfs-namespaces)