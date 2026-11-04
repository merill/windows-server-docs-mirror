---
layout: Conceptual
title: Choose a Namespace Type | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/choose-a-namespace-type
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to choose a namespace type.
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 45272cab-5fbf-be85-4007-eea894d9a29e
document_version_independent_id: ee1fecdd-8b09-ffdb-f1a3-b8e2d6647ac9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/choose-a-namespace-type.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/choose-a-namespace-type
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/choose-a-namespace-type.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 926a920e-55fe-bc98-6a55-ed0fd79de606
---

# Choose a Namespace Type | Microsoft Learn

When creating a namespace, you must choose one of two namespace types: a stand-alone namespace or a domain-based namespace. In addition, if you choose a domain-based namespace, you must choose a namespace mode: Windows 2000 Server mode or Windows Server 2008 mode.

## Choosing a namespace type

Choose a stand-alone namespace if any of the following conditions apply to your environment:

- Your organization does not use Active Directory Domain Services (AD DS).
- You want to increase the availability of the namespace by using a failover cluster.
- You need to create a single namespace with more than 5,000 DFS folders in a domain that does not meet the requirements for a domain-based namespace (Windows Server 2008 mode) as described later in this topic.

Note

To check the size of a namespace, right-click the namespace in the DFS Management console tree, click **Properties**, and then view the namespace size in the **Namespace Properties** dialog box. For more information about DFS Namespace scalability, see the Microsoft website [File Services](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771548%28v=ws.10%29).

Choose a domain-based namespace if any of the following conditions apply to your environment:

- You want to ensure the availability of the namespace by using multiple namespace servers.
- You want to hide the name of the namespace server from users. This makes it easier to replace the namespace server or migrate the namespace to another server.

## Choosing a domain-based namespace mode

If you choose a domain-based namespace, you must choose whether to use the Windows 2000 Server mode or the Windows Server 2008 mode. The Windows Server 2008 mode includes support for access-based enumeration and increased scalability. The domain-based namespace introduced in Windows 2000 Server is now referred to as "domain-based namespace (Windows 2000 Server mode)."

To use the Windows Server 2008 mode, the domain and namespace must meet the following minimum requirements:

- The forest uses the Windows Server 2003 or higher forest functional level.
- The domain uses the Windows Server 2008 or higher domain functional level.
- All namespace servers are running Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, or Windows Server 2008.

If your environment supports it, choose the Windows Server 2008 mode when you create new domain-based namespaces. This mode provides additional features and scalability, and also eliminates the possible need to migrate a namespace from the Windows 2000 Server mode.

For information about migrating a namespace to Windows Server 2008 mode, see [Migrate a Domain-based Namespace to Windows Server 2008 Mode](migrate-a-domain-based-namespace-to-windows-server-2008-mode).

If your environment does not support domain-based namespaces in Windows Server 2008 mode, use the existing Windows 2000 Server mode for the namespace.

## Comparing namespace types and modes

The characteristics of each namespace type and mode are described in the following table.

| Characteristic | Stand-Alone Namespace | Domain-based Namespace (Windows 2000 Server Mode) | Domain-based Namespace (Windows Server 2008 Mode) |
| --- | --- | --- | --- |
| Path to namespace | \\ *ServerName\RootName* | \\ *NetBIOSDomainName\RootName*\\ *DNSDomainName\RootName* | \\ *NetBIOSDomainName\RootName* \\ *DNSDomainName\RootName* |
| Namespace information storage location | In the registry and in a memory cache on the namespace server | In AD DS and in a memory cache on each namespace server | In AD DS and in a memory cache on each namespace server |
| Namespace size recommendations | The namespace can contain more than 5,000 folders with targets; the recommended limit is 50,000 folders with targets | The size of the namespace object in AD DS should be less than 5 megabytes (MB) to maintain compatibility with domain controllers that are not running Windows Server 2008. This means no more than approximately 5,000 folders with targets. | The namespace can contain more than 5,000 folders with targets; the recommended limit is 50,000 folders with targets |
| Minimum AD DS forest functional level | AD DS is not required | Windows 2000 | Windows Server 2003 |
| Minimum AD DS domain functional level | AD DS is not required | Windows 2000 mixed | Windows Server 2008 |
| Minimum supported namespace servers | Windows 2000 Server | Windows 2000 Server | Windows Server 2008 |
| Support for access-based enumeration (if enabled) | Yes, requires Windows Server 2008 namespace server | No | Yes |
| Supported methods to ensure namespace availability | Create a stand-alone namespace on a failover cluster. | Use multiple namespace servers to host the namespace. (The namespace servers must be in the same domain.) | Use multiple namespace servers to host the namespace. (The namespace servers must be in the same domain.) |
| Support for using DFS Replication to replicate folder targets | Supported when joined to an AD DS domain | Supported | Supported |

## Additional References

- [Deploying DFS Namespaces](deploying-dfs-namespaces)
- [Migrate a Domain-based Namespace to Windows Server 2008 Mode](migrate-a-domain-based-namespace-to-windows-server-2008-mode)