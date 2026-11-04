---
layout: Conceptual
title: Enable Access-based Enumeration on a Namespace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/enable-access-based-enumeration-on-a-namespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to enable access-based enumeration on a namespace.
ms.date: 2017-06-05T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 500689c7-a041-052e-8c49-688eda932556
document_version_independent_id: 5b6271b1-d909-6e9f-1049-040077e8e876
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/enable-access-based-enumeration-on-a-namespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/enable-access-based-enumeration-on-a-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/enable-access-based-enumeration-on-a-namespace.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ff3509f6-5853-77a8-e947-43559546a8e1
---

# Enable Access-based Enumeration on a Namespace | Microsoft Learn

Access-based enumeration hides files and folders that users do not have permissions to access. By default, this feature is not enabled for DFS namespaces. You can enable access-based enumeration of DFS folders by using DFS Management. To control access-based enumeration of files and folders in folder targets, you must enable access-based enumeration on each shared folder by using Share and Storage Management.

To enable access-based enumeration on a namespace, all namespace servers must be running Windows Server 2008 or newer. Additionally, domain-based namespaces must use the Windows Server 2008 mode. For information about the requirements of the Windows Server 2008 mode, see [Choose a Namespace Type](choose-a-namespace-type).

In some environments, enabling access-based enumeration can cause high CPU utilization on the server and slow response times for users.

Note

If you upgrade the domain functional level to Windows Server 2008 while there are existing domain-based namespaces, DFS Management will allow you to enable access-based enumeration on these namespaces. However, you will not be able to edit permissions to hide folders from any groups or users unless you migrate the namespaces to the Windows Server 2008 mode. For more information, see [Migrate a Domain-based Namespace to Windows Server 2008 Mode](migrate-a-domain-based-namespace-to-windows-server-2008-mode).

To use access-based enumeration with DFS Namespaces, you must follow these steps:

- Enable access-based enumeration on a namespace
- Control which users and groups can view individual DFS folders

Warning

Access-based enumeration does not prevent users from getting a referral to a folder target if they already know the DFS path. Only the share permissions or the NTFS file system permissions of the folder target (shared folder) itself can prevent users from accessing a folder target. DFS folder permissions are used only for displaying or hiding DFS folders, not for controlling access, making Read access the only relevant permission at the DFS folder level. For more information, see [Using Inherited Permissions with Access-Based Enumeration](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd834874%28v=ws.11%29)
 You can enable access-based enumeration on a namespace either by using the Windows interface or by using a command line. 
## To enable access-based enumeration by using the Windows interface

1. In the console tree, under the **Namespaces** node, right-click the appropriate namespace and then click **Properties** .
2. Click the **Advanced** tab and then select the **Enable access-based enumeration for this namespace** check box.

## To enable access-based enumeration by using a command line

1. Open a command prompt window on a server that has the **Distributed File System** role service or **Distributed File System Tools** feature installed.
2. Type the following command, where *&lt;namespace\_root&gt;* is the root of the namespace:

    ```
    dfsutil property abe enable \\ <namespace_root>
    ```

Tip

To manage access-based enumeration on a namespace by using Windows PowerShell, use the [Set-DfsnRoot](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd834874%28v=ws.11%29), [Grant-DfsnAccess](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd834874%28v=ws.11%29), and [Revoke-DfsnAccess](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd834874%28v=ws.11%29) cmdlets. The DFSN Windows PowerShell module was introduced in Windows Server 2012.

You can control which users and groups can view individual DFS folders either by using the Windows interface or by using a command line.

## To control folder visibility by using the Windows interface

1. In the console tree, under the **Namespaces** node, locate the folder with targets for which you want to control visibility, right-click it and then click **Properties**.
2. Click the **Advanced** tab.
3. Click **Set explicit view permissions on the DFS folder** and then **Configure view permissions**.
4. Add or remove groups or users by clicking **Add** or **Remove**.
5. To allow users to see the DFS folder, select the group or user, and then select the **Allow** check box.

    To hide the folder from a group or user, select the group or user, and then select the **Deny** check box.

## To control folder visibility by using a command line

1. Open a Command Prompt window on a server that has the **Distributed File System** role service or **Distributed File System Tools** feature installed.
2. Type the following command, where *&lt;DFSPath&gt;* is the path of the DFS folder (link), *&lt;DOMAIN\Account&gt;* is the name of the group or user account, and *(...)* is replaced with additional Access Control Entries (ACEs):

    ```
    dfsutil property sd grant <DFSPath> DOMAIN\Account:R (...) Protect Replace
    ```

    For example, to replace existing permissions with permissions that allows the Domain Admins and CONTOSO\Trainers groups Read (R) access to the \contoso.office\public\training folder, type the following command:

    ```
    dfsutil property sd grant \\contoso.office\public\training "CONTOSO\Domain Admins":R CONTOSO\Trainers:R Protect Replace
    ```
3. To perform additional tasks from the command prompt, use the following commands:

| Command | Description |
| --- | --- |
| [Dfsutil property sd deny](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759150%28v=ws.11%29) | Denies a group or user the ability to view the folder. |
| [Dfsutil property sd reset](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759150%28v=ws.11%29) | Removes all permissions from the folder. |
| [Dfsutil property sd revoke](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759150%28v=ws.11%29) | Removes a group or user ACE from the folder. |

## Additional References

- [Create a DFS Namespace](create-a-dfs-namespace)
- [Delegate Management Permissions for DFS Namespaces](delegate-management-permissions-for-dfs-namespaces)
- [Installing DFS](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731089%28v=ws.11%29)
- [Using Inherited Permissions with Access-Based Enumeration](using-inherited-permissions-with-access-based-enumeration)