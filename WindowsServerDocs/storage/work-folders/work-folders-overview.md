---
layout: Conceptual
title: Work Folders overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/work-folders/work-folders-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-16T00:00:00.0000000Z
description: Learn how Work Folders provides a consistent way for users to access work files from PCs and devices in Windows.
locale: en-us
document_id: d4132d5c-20d3-6ba3-3558-34c379c35229
document_version_independent_id: 3ac614ac-d52a-9c4e-4ac5-05ceafcd7a31
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/work-folders/work-folders-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/work-folders/work-folders-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/work-folders/work-folders-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 9c0860fe-941b-2383-8b0e-5cc656049c6f
---

# Work Folders overview | Microsoft Learn

Work Folders is a Windows Server role service for file servers. Work Folders provides a consistent way for users to access their work files from their PCs and devices.

With Work Folders, users can store and access work files on personal computers and devices, often referred to as bring-your-own device (BYOD), in addition to corporate PCs. Users gain a convenient location to store work files, and they can access those files from anywhere. Organizations use Work Folders to help maintain control over corporate data. They can store files on centrally managed file servers, and define user device policies like encryption and lock-screen passwords.

You can deploy Work Folders with existing deployments of Folder Redirection, Offline Files, and home folders. Work Folders stores user files in a folder on the server called a *sync share*. Specify a folder that already contains user data, which enables you to adopt Work Folders without migrating servers, and data, or immediately phasing out your existing solution.

## Common uses

Administrators can use Work Folders to provide users with access to their work files while keeping centralized storage and control over the organization's data. Work Folders can also accomplish these specific applications:

- Provide a single point of access to work files from a user's work and personal computers and devices.
- Access work files while offline and then sync with the central file server when the PC or device next has internet or intranet connectivity.
- Deploy with existing deployments of Folder Redirection, Offline Files, and home folders.
- Use existing file server management technologies, such as file classification and folder quotas, to manage user data.
- Specify security policies to instruct user's PCs and devices to encrypt Work Folders and use a lock screen password.
- Use Failover Clustering with Work Folders to provide a high-availability solution.

## Features

Work Folders provides users with multiple ways to access, manage, and share work files. The following table describes the primary features of Work Folders:

- **Role service in Server Manager**: File and Storage Services provides a way to set up sync shares (folders that store user's work files), monitors Work Folders, and manages sync shares and user access.
- **Work Folders cmdlets**: Windows PowerShell module contains comprehensive cmdlets for managing Work Folders servers.
- **Work Folders integration with Windows**: Work Folders provides the following functionality in Windows 10, and Windows 11.
- **Work Folders app for devices**: Mobile apps allow popular devices to access files in Work Folders.

## Software requirements

Work Folders requires specific software depending on the operating system and version on which it's run. The following section lists the requirements and optional supporting services.

### Requirements for file servers and network infrastructure

- **Server requirement.** A server running at least Windows Server 2012 R2.
- **Volume requirement.** A volume formatted with the NTFS file system for storing user files.
- **Password enforcement policy.** To enforce password policies on Windows PCs, you must use Group Policy password policies.
- **A server certificate.** There must be a server certificate for each file server hosting Work Folders. These certificates should be from a Certification Authority (CA) that's trusted by your users. Ideally a public CA.
- **(Optional) An Active Directory Domain Services forest.** Use this forest with the schema extensions in Windows Server to support automatically referring PCs and devices to the correct file server when you use multiple file servers.

### Requirements for enabling users to sync across the internet

- **Server accessibility.** The ability to make a server accessible from the internet by creating publishing rules in your organization's reverse proxy or network gateway.
- **(Optional) Domain name.** A publicly registered domain name and the ability to create more public DNS records for the domain.
- **(Optional) Infrastructure.** Active Directory Federation Services (AD FS) infrastructure when you use AD FS authentication.

### Requirements for client computers

- Computers must run one of the following operating systems: Windows 10, or Windows 11..
- Enough free space on a local, NTFS-formatted drive to store all the user's files in Work Folders, plus 6 more GB of free space if Work Folders is located on the system drive, as it is by default. Work Folders uses the following location by default: **%USERPROFILE%\Work Folders**

    However, users can change the location during setup. microSD cards and USB drives formatted with the NTFS file system are supported locations. Sync stops if the drives are removed.

    The maximum size for individual files is 10 GB by default. There's no per-user storage limit. However, administrators can use the quotas functionality of File Server Resource Manager to implement quotas.
- Work Folders doesn't support rolling back the virtual machine state of client virtual machines. Instead perform backup and restore operations from inside the client virtual machine by using System Image Backup or another backup app.

## Comparison with other sync technologies

The following table discusses how various Microsoft sync technologies are positioned and when to use each.

| - | Work Folders | Offline Files | OneDrive for Business | OneDrive |
| --- | --- | --- | --- | --- |
| **Technology summary** | Syncs files that are stored on a file server with PCs and devices | Syncs files that are stored on a file server with PCs that have access to the corporate network (can be replaced by Work Folders) | Syncs files that are stored in Microsoft 365 or in SharePoint with PCs and devices inside or outside a corporate network, and provides document collaboration functionality | Syncs personal files that are stored in OneDrive with PCs, Mac computers, and devices |
| **Intended to provide user access to work files** | Yes | Yes | Yes | No |
| **Cloud service** | None | None | Microsoft 365 | Microsoft OneDrive |
| **Internal network servers** | File servers running Windows Server 2012 R2, Windows Server 2016, and Windows Server 2019 | File servers | SharePoint server (optional) | None |
| **Supported clients** | PCs, iOS | PCs in a corporate network or connected through DirectAccess, VPNs, or other remote access technologies | PCs, iOS, Android, Windows Phone | PCs, Mac computers, Windows Phone, iOS, Android |

Note

In addition to the sync technologies listed in the previous table, Microsoft offers other replication technologies, including DFS Replication, which is designed for server-to-server replication, and BranchCache, which is designed as a branch office WAN acceleration technology. For more information, see the [DFS Namespaces overview](/en-us/windows-server/storage/dfs-namespaces/dfs-overview), [DFS Replication overview](/en-us/windows-server/storage/dfs-replication/dfsr-overview), and [BranchCache Overview](/en-us/windows-server/networking/branchcache/branchcache).

## Server Manager

Work Folders is part of the File and Storage Services role. You can install the **Work Folders** role service by using the Add Roles and Features Wizard. On the Select server roles page, expand File and Storage Services, then expand File and iSCSI Services, then select Work Folders.

Or use the [Install-WindowsFeature](/en-us/powershell/module/servermanager/install-windowsfeature) cmdlet to install Work Folders using PowerShell. You must be run a Windows PowerShell session as an administrator to use this cmdlet.

The following command installs all the all subordinate role services, including Work Folders, and will include management tools such as snap-ins on the target server.

```powershell
Install-WindowsFeature -Name File-Services -IncludeAllSubFeature -IncludeManagementTools
```

Both methods accomplish the following tasks:

- Add the **Work Folders** page to **File and Storage Services** in Server Manager.
- Install the Windows Sync Shares service, which is used by Windows Server to host sync shares.
- Install the SyncShare Windows PowerShell module to manage Work Folders on the server.