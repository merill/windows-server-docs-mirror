---
layout: Conceptual
title: Add Namespace Servers to a Domain-based DFS Namespace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/add-namespace-servers-to-a-domain-based-dfs-namespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to specify additional namespace servers to host a namespace using DFS management.
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 69ca779c-2821-3c9a-fdd9-d447c883fe3a
document_version_independent_id: 3ead984c-c7c9-f53f-c3c6-6d1d1e650dc7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/add-namespace-servers-to-a-domain-based-DFS-namespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/add-namespace-servers-to-a-domain-based-dfs-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/add-namespace-servers-to-a-domain-based-DFS-namespace.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2201367a-06d9-b425-c66d-85a51001c072
---

# Add Namespace Servers to a Domain-based DFS Namespace | Microsoft Learn

You can increase the availability of a domain-based namespace by specifying additional namespace servers to host the namespace.

## To add a namespace server to a domain-based namespace

To add a namespace server to a domain-based namespace using DFS Management, use the following procedure:

1. Click **Start**, point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, right-click a domain-based namespace, and then click **Add Namespace Server**.
3. Enter the path to another server, or click **Browse** to locate a server.

Note

This procedure is not applicable for stand-alone namespaces because they support only a single namespace server. To increase the availability of a stand-alone namespace, specify a failover cluster as the namespace server in the New Namespace Wizard.

Tip

To add a namespace server by using Windows PowerShell, use the [New-DfsnRootTarget cmdlet](/en-us/powershell/module/dfsn/new-dfsnroottarget). The DFSN Windows PowerShell module was introduced in Windows Server 2012.

## Additional References

- [Deploying DFS Namespaces](deploying-dfs-namespaces)
- [Review DFS Namespaces Server Requirements](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753448%28v=ws.11%29)
- [Create a DFS Namespace](create-a-dfs-namespace)
- [Delegate Management Permissions for DFS Namespaces](delegate-management-permissions-for-dfs-namespaces)