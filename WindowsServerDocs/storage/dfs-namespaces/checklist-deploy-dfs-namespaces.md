---
layout: Conceptual
title: Checklist Deploy DFS Namespaces | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/checklist-deploy-dfs-namespaces
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to configure and deploy DFS Namespaces.
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: checklist
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 97c64b76-c53e-65a4-2bee-11a478d1a93b
document_version_independent_id: 2b53da59-b135-bfee-43fb-4d1d90b9d7f7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/checklist-deploy-dfs-namespaces.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/checklist-deploy-dfs-namespaces
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/checklist-deploy-dfs-namespaces.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ad927bb8-6d9e-9708-c4f3-6e1380921f31
---

# Checklist Deploy DFS Namespaces | Microsoft Learn

Distributed File System (DFS) Namespaces and DFS Replication can be used to publish documents, software, and line-of-business data to users throughout an organization. Although DFS Replication alone is sufficient to distribute data, you can use DFS Namespaces to configure the namespace so that a folder is hosted by multiple servers, each of which holds an updated copy of the folder. This increases data availability and distributes the client load across servers.

When browsing a folder in the namespace, users are not aware that the folder is hosted by multiple servers. When a user opens the folder, the client computer is automatically referred to a server on its site. If no same-site servers are available, you can configure the namespace to refer the client to a server that has the lowest connection cost as defined in Active Directory Directory Services (AD DS).

To deploy DFS Namespaces, perform the following tasks:

- Review the concepts, and requirements of DFS Namespaces. [Overview of DFS Namespaces](dfs-overview)
- [Choose a namespace type](choose-a-namespace-type)
- [Create a DFS namespace](create-a-dfs-namespace)
- Migrate existing domain-based namespaces to Windows Server 2008 mode domain-based namespaces. [Migrate a Domain-based Namespace to Windows Server 2008 mode](migrate-a-domain-based-namespace-to-windows-server-2008-mode)
- Increase availability by adding namespace servers to a domain-based namespace. [Add Namespace Servers to a Domain-based DFS Namespace](add-namespace-servers-to-a-domain-based-dfs-namespace)
- Add folders to a namespace. [Create a Folder in a DFS Namespace](create-a-folder-in-a-dfs-namespace)
- Add folder targets to folders in a namespace. [Add Folder Targets](add-folder-targets)
- Replicate content between folder targets using DFS Replication (optional). [Replicate Folder Targets Using DFS Replication](replicate-folder-targets-using-dfs-replication)

## Additional References

- [Namespaces](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771914%28v=ws.11%29)
- [Checklist: Tune a DFS Namespace](checklist-tune-a-dfs-namespace)
- [Replication](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770278%28v=ws.11%29)