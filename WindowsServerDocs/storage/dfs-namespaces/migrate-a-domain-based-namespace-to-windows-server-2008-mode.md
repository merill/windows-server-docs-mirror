---
layout: Conceptual
title: Migrate a Domain-based Namespace to Windows Server 2008 Mode | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/migrate-a-domain-based-namespace-to-windows-server-2008-mode
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to migrate a domain-based namespace to Windows Server 2008 mode
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: upgrade-and-migration-article
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 6e0ae24b-fa32-77a7-8fbf-2dd91085a110
document_version_independent_id: e5a1bb8a-6433-7530-c751-93ae3ff76cb3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/migrate-a-domain-based-namespace-to-windows-server-2008-mode.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/migrate-a-domain-based-namespace-to-windows-server-2008-mode
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/migrate-a-domain-based-namespace-to-windows-server-2008-mode.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 10e717d9-f024-940a-24eb-ca2f0f5a1609
---

# Migrate a Domain-based Namespace to Windows Server 2008 Mode | Microsoft Learn

The Windows Server 2008 mode for domain-based namespaces includes support for access-based enumeration and increased scalability.

## To migrate a domain-based namespace to Windows Server 2008 mode

To migrate a domain-based namespace from Windows 2000 Server mode to Windows Server 2008 mode, you must export the namespace to a file, delete the namespace, re-create it in Windows Server 2008 mode, and then import the namespace settings. To do so, use the following procedure:

1. Open a Command Prompt window and type the following command to export the namespace to a file, where \\*domain*\*namespace* is the name of the appropriate domain, and namespace and *path\filename* is the path and file name of the file for export:

    ```
    Dfsutil root export \\domain\namespace path\filename.xml
    ```
2. Write down the path ( \\*server* \*share* ) for each namespace server. You must manually add namespace servers to the re-created namespace because Dfsutil cannot import namespace servers.
3. In DFS Management, right-click the namespace and then click **Delete**, or type the following command at a command prompt,  where \\*domain*\*namespace* is the name of the appropriate domain and namespace:

    ```
    Dfsutil root remove \\domain\namespace
    ```
4. In DFS Management, re-create the namespace with the same name, but use the Windows Server 2008 mode, or type the following command at a command prompt, where  \\*server*\*namespace* is the name of the appropriate server and share for the namespace root:

    ```
    Dfsutil root adddom \\server\namespace v2
    ```
5. To import the namespace from the export file, type the following command at a command prompt, where  \\*domain*\*namespace* is the name of the appropriate domain and namespace and *path\filename* is the path and file name of the file to import:

    ```
    Dfsutil root import merge path\filename.xml \\domain\namespace
    ```

    Note

    To minimize the time required to import a large namespace, run the **Dfsutil** root import command locally on a namespace server.
6. Add any remaining namespace servers to the re-created namespace by right-clicking the namespace in DFS Management and then clicking **Add Namespace Server**, or by typing the following command at a command prompt, where  \\*server*\*share* is the name of the appropriate server and share for the namespace root:

    ```
    Dfsutil target add \\server\share
    ```

    Note

    You can add namespace servers before importing the namespace, but doing so causes the namespace servers to incrementally download the metadata for the namespace instead of immediately downloading the entire namespace after being added as a namespace server.

## Additional References

- [Deploying DFS Namespaces](deploying-dfs-namespaces)
- [Choose a Namespace Type](choose-a-namespace-type)