---
layout: Conceptual
title: Create a DFS Namespace in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-namespaces/create-a-dfs-namespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Use
ms.date: 2025-04-03T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ai-usage: ai-assisted
locale: en-us
document_id: d7572800-ac08-d2e8-59c3-f83f067ec5f2
document_version_independent_id: b6d35e71-ca3b-275a-aea7-62336c0c380b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-namespaces/create-a-dfs-namespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-namespaces/create-a-dfs-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-namespaces/create-a-dfs-namespace.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 3cb38bd8-250a-57f9-cbcb-8d371d280cf0
---

# Create a DFS Namespace in Windows Server | Microsoft Learn

This article describes how to create a Distributed File System (DFS) namespace in Windows Server. A DFS namespace is a virtual view of shared folders in an organization. It allows users to access shared folders using a single path, regardless of the physical location of the shared folders.

To create a new namespace, you can use Server Manager to create the namespace when you install the Distributed File System (DFS) Namespaces role service or the [New-DfsnRoot](/en-us/powershell/module/dfsn/new-dfsnroot) PowerShell cmdlet.

## Prerequisites

Before you create a DFS Namespace, ensure that you have the following prerequisites:

- You must be a member of the **Administrators** group, or equivalent, on the computer where you're creating the namespace. To learn more, about the delegation of permissions required to create a namespace, see [Delegate management permissions for DFS Namespaces](delegate-management-permissions-for-dfs-namespaces).
- You must have the **DFS Namespaces** role service installed on the computer where you're creating the namespace.
- For both stand-alone and domain-based namespaces, ensure the namespace location is secure. This location can be the default path (*C:\DFSRoots*) or a custom path specified by the administrator during namespace creation. Restrict access to authorized users only. Doing so helps protect the configuration and reduces the risk of misuse or exploitation.

## Create the namespace

To create a DFS namespace, you can use the **DFS Management** console or the **New-DfsnRoot** PowerShell cmdlet. Select the method that best suits your needs.

# [DFS Management console](#tab/dfs-management-console)
The following procedure describes how to create a namespace using the DFS Management console.

1. Select **Start**, point to **Administrative Tools**, and then select **DFS Management**.
2. In the console tree, right-click the **Namespaces** node, and then select **New Namespace**.
3. On the **Namespace Server** screen, select the server on which you want to create the namespace, then select **Next**.
4. Enter the new namespace name in the **Name** box on the **Namespace Name and Settings** screen, then select **Next**.
5. Select the type of namespace you want to create on the **Namespace Type** screen. You can choose between a domain-based namespace or a stand-alone namespace. Make your selection, and then select **Next**.

    Important

    Don't attempt to create a domain-based namespace using the Windows Server 2008 mode unless the forest functional level is Windows Server 2003 or higher. Doing so can result in a namespace for which you can't delete DFS folders, yielding the following error message: "The folder can't be deleted. Can't complete this function."
6. On the **Review Settings and Create Namespace** screen, review the settings for the namespace. If everything looks correct, select **Create** to create the namespace.
7. Wait for the namespace to be created. This process might take a few minutes, depending on your environment. Once the namespace is created, you see a message indicating that the namespace was created successfully. Select **Close** to close the wizard.

# [PowerShell](#tab/powershell)
The following procedure describes how to create a namespace using the **New-DfsnRoot** PowerShell cmdlet.

1. Open an elevated **Windows PowerShell** as an administrator.
2. Create a folder to serve as the root of the namespace. For example, you can create a folder named **C:\DFSRoots&lt;namespace&gt;**. Use the following command replacing `<NamespaceName>` with the name of your namespace:

    ```powershell
    New-Item -Path "C:\DFSRoots\<NamespaceName>" -ItemType Directory
    ```
3. Share the newly created folder. Use the following command replacing `<NamespaceName>` with the name of your namespace:

    ```powershell
    New-SmbShare -Name "<NamespaceName>" -Path "C:\DFSRoots\<NamespaceName>" -ReadAccess "<domainFQDN>\<groupName>"
    ```

    Note

    The `-ReadAccess` parameter specifies read access to the DFS Namespace root share only for users in the group.
4. To create a DFS Namespace, use one of the following steps. Replace `<ServerName>`, `<DomainName>`, `<NamespaceName>`, `<TargetHost>`, and `<TargetPath>` with the appropriate values for your environment.

    1. To create a stand-alone namespace, use the following command:

    ```powershell
    New-DfsnRoot -Path "\\<ServerName>\<NamespaceName>" -TargetPath "<TargetPath>" -Type Standalone
    ```

    OR

    1. To create a domain-based namespace, use the following command:

    ```powershell
    New-DfsnRoot -Path "\\<DomainName>\<NamespaceName>" -TargetPath "\\<TargetHost>\<TargetPath>" -Type DomainV2
    ```
5. To verify that the namespace was created successfully, use the following command:

    ```powershell
    Get-DfsnRoot
    ```

    This command displays a list of all DFS namespaces on the server, including the one you created.

---

## Secure the namespace

After creating the namespace, you should secure it by restricting access to the namespace folder. You should secure both the stand-alone and domain-based namespaces. Securing the namespace is important to maintain configuration integrity and mitigate the risk of exploitation.

To secure the namespace, you can use the following procedure:

1. In **Windows Explorer**, navigate to the namespace folder (for example, *C:\DFSRoots\My Namespace*).
2. Right-click the folder, and then select **Properties**.
3. On the **Security** tab, select **Advanced**.
4. In the **Advanced Security Settings** dialog box, select **Change Permissions**, then select **Disable Inheritance**.
5. Select **Convert inherited permissions into explicit permissions on this object** to convert the inherited permissions into explicit permissions.
6. Remove any groups or users that shouldn't have access to the namespace folder. For example, remove the **CREATOR OWNER** principle with **Full control** access. Also remove **Users** groups with the **Special** access privilege. This entry is added by default and allows all users to create files and folders in the namespace folder.

    Note

    Permissions are inherited from the parent folder. Permissions for the namespace root folder are independent of the permissions for the target folders. You must set permissions for the namespace root folder and the target folders separately.