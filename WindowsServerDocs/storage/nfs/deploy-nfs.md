---
layout: Conceptual
title: Deploy Network File System | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/nfs/deploy-nfs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Step-by-step guide to deploying NFS on Windows Server, including installation, authentication methods, and file share creation.
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-16T00:00:00.0000000Z
locale: en-us
document_id: e3e1c909-4060-8150-9052-7aa0c4c83ab7
document_version_independent_id: 0cc481af-638f-e4e9-0969-2338e3817215
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/nfs/deploy-nfs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/nfs/deploy-nfs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/nfs/deploy-nfs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 901280e8-ce73-8213-c280-20f3e132f995
---

# Deploy Network File System | Microsoft Learn

Network File System (NFS) provides a file sharing solution that lets you transfer files between computers running Windows Server and UNIX operating systems by using the NFS protocol. This article describes the steps you should follow to install NFS and create your first NFS share.

## NFS authentication

NFS Server for Windows Server supports multiple authentication methods, including Kerberos and AUTH\_SYS. The authentication method you choose depends on your organization's security requirements and the NFS version you're using. Consider which authentication method is best for your environment before creating an NFS file share.

For the NFS version 4.1 and NFS version 3.0 protocols, we recommend that you use Kerberos (RPCSEC\_GSS). There are three options with increasing levels of security protection:

- **Krb5**: Uses the Kerberos version 5 protocol to authenticate users before granting them access to the file share.
- **Krb5i**: Uses the Kerberos version 5 protocol to authenticate with integrity checking (checksums), which verifies that the data isn't altered.
- **Krb5p**: Uses the Kerberos version 5 protocol, which authenticates NFS traffic with encryption for privacy. This option is the most secure Kerberos option.

    Note

    You can also choose not to use the preceding Kerberos authentication methods and instead enable unmapped user access through AUTH\_SYS. We *strongly discourage* using this option as it removes all authentication protections and allows any user with access to the NFS server to access data. When you use unmapped user access, you can specify to allow unmapped user access by UID or GID, which is the default. You can also allow anonymous access.

## Prerequisites

To deploy NFS, ensure that you have the following prerequisites:

- One or more computers running Windows Server on which you install the two main Services for NFS components: Server for NFS and Client for NFS. You can install these components on the same computer or on different computers.
- If you're using a UNIX-based computer for your NFS server or client, it must be compatible with one of the following NFS protocol specifications:

    - NFS Version 4.1 Protocol Specification, as defined in [RFC5661](https://tools.ietf.org/html/rfc5661)
    - NFS Version 3 Protocol Specification, as defined in [RFC1813](https://tools.ietf.org/html/rfc1813)
    - NFS Version 2 Protocol Specification, as defined in [RFC1094](https://tools.ietf.org/html/rfc1094)

### Install Network File System

To install the Network File System role as a standalone server, perform the following steps:

# [GUI](#tab/gui)
Here's how to install the DNS Server role using Server Manager from the Windows desktop.

1. From the Windows desktop, open the **Start** menu, then select the **Server Manager** tile.
2. On the menu, go to **Manage**, and then select **Add Roles and Features**.
3. On the **Before you begin** page, select **Next** to begin.
4. On the **Select installation type** page, select the **Role-based or feature-based installation** option, and select **Next**.
5. On the **Select destination server** page, leave the default options. Select **Next**.
6. On the **Select server roles** page, expand **File and Storage Services &gt; File and iSCSI Services**, check **File Server**, **File Server Resource Manager**, and **Server for NFS**, then **Next**.

    1. You're prompted to add features that are required for Server for NFS, if you're happy with the defaults, select **Add Features**.
7. On the **Select features** page, you can leave the default selections, and then select on the **Next** button.
8. On the **DNS Server** page, review the role description and things to note, select **Next** to continue.
9. On the **Confirm installation selections** page, review the selected roles and features, and then select on the **Install** button to begin the installation process.
10. Once the installation is complete, select **Close**. The installation doesn't require a reboot.

# [PowerShell](#tab/powershell)
Here's how to install the DNS Server role using the [Install-WindowsFeature](/en-us/powershell/module/servermanager/install-windowsfeature) command.

1. Run PowerShell on your computer in an elevated session.
2. To install the DNS role, run the following command. The installation doesn't require a reboot.

    ```powershell
    Install-WindowsFeature -Name FS-NFS-Service -IncludeManagementTools
    ```

---

## Create an NFS file share

To create an NFS file share, perform the following steps.

Tip

NFS version 4.1 allows file names to be created or copied with illegal characters. If you attempt to open the files with vi editor, it shows the files as being corrupt. You can't save the file from vi, rename, move it, or change permissions. Avoid using illegal characters.

# [GUI](#tab/gui)
Here's how to create an NFS file share using Server Manager from the Windows desktop.

1. Sign in to the server as a member of the local Administrators group.
2. Server Manager starts automatically.

    - If the tool doesn't automatically start, select **Start**. Enter **servermanager.exe**, and then select **Server Manager**.
3. On the left, select **File and Storage Services**, then select **Shares**.
4. Under the **Shares** column, in the **Tasks** drop down menu, select **New Share**.
5. On the **Select Profile** page, select either **NFS Share - Quick** or **NFS Share - Advanced**, then select **Next**.
6. On the **Share Location** page, select a server and a volume, then select **Next**.
7. On the **Share Name** page, enter a name for the new share. Confirm the share path and remote path, then select **Next**.
8. On the **Authentication** page, specify the authentication method you want to use, then select **Next**. Share authentication methods are discussed in the NFS authentication section.
9. On the **Share Permissions** page, select **Add**. The **Add Permissions** dialog opens.

    1. Choose the level of user permissions to grant: **Host**, **Netgroup**, **Client group**, or **All Machines**.
    2. Use the drop-down menu to select the preferred **Language encoding**.
    3. Use the drop-down menu to select the preferred **Share permissions**.
    4. Select **Add**, then select **Next**.
10. On the **Permissions** page, configure access control for your selected users. When you're ready, select **Next**.
11. On the **Confirmation** page, review your configuration, and select **Create** to create the NFS file share.

# [PowerShell](#tab/powershell)
Here's how to create a new NFS share using the [New-NfsShare](/en-us/powershell/module/nfs/new-nfsshare) command.

1. Run PowerShell on your computer in an elevated session.
2. Create a folder to serve as the share. For example, you can create a folder named **C:\Shares&lt;sharename&gt;**. Use the following command replacing `<sharename>` with the name of your namespace:

    ```powershell
    New-Item -Path "C:\Shares\<sharename>" -ItemType Directory
    ```
3. Share the newly created folder with read/write access and using krb5 authentication. Use the following command replacing `<sharename>` with the name of your share:

    ```powershell
    New-NfsShare -Name "<sharename>" -Path "C:\Shares\<sharename>" -Authentication krb5 -Permission ReadWrite
    ```

---