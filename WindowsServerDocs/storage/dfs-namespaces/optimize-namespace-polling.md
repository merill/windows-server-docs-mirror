---
layout: Conceptual
title: Optimize Namespace Polling | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/optimize-namespace-polling
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to optimize namespace polling to maintain a consistent domain-based namespace across namespace servers
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: aef82549-877a-6596-ac05-fc138e65e2a8
document_version_independent_id: 7e871dcb-00fe-4f49-2091-2a41f5fbfb10
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/optimize-namespace-polling.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/optimize-namespace-polling
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/optimize-namespace-polling.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 4db6df6a-3fd1-ad6f-6015-0c8b35d95166
---

# Optimize Namespace Polling | Microsoft Learn

To maintain a consistent domain-based namespace across namespace servers, it is necessary for namespace servers to periodically poll Active Directory Domain Services (AD DS) to obtain the most current namespace data.

## To optimize namespace polling

Use the following procedure to optimize how namespace polling occurs:

1. Click **Start**, point to **Administrative Tools**, and then click **DFS Management**.
2. In the console tree, under the **Namespaces** node, right-click a domain-based namespace, and then click **Properties** .
3. On the **Advanced** tab, select whether you want the namespace optimized for consistency or scalability.

    - Choose **Optimize for consistency** if there are 16 or fewer namespace servers hosting the namespace.
    - Choose **Optimize for scalability** if there are more than 16 namespace servers. This reduces the load on the Primary Domain Controller (PDC) Emulator, but increases the time required for changes to the namespace to replicate to all namespace servers. Until changes replicate to all servers, users might have an inconsistent view of the namespace.

Note

To set the namespace polling mode by using Windows PowerShell, use the [Set-DfsnRoot EnableRootScalability](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771913%28v=ws.11%29) cmdlet, which was introduced in Windows Server 2012.

## Additional References

- [Tuning DFS Namespaces](tuning-dfs-namespaces)
- [Delegate Management Permissions for DFS Namespaces](delegate-management-permissions-for-dfs-namespaces)