---
layout: Conceptual
title: Folder Redirection and Roaming User Profiles in Windows and Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/folder-redirection/folder-redirection-rup-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Discover how Folder Redirection and Roaming User Profiles centralize user data and synchronize profiles across devices.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-15T00:00:00.0000000Z
locale: en-us
document_id: d2961a5f-45c3-6bc9-c1a0-0b16e3b9ed62
document_version_independent_id: f7dfd602-28c7-72ea-e88d-b78af9841844
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/folder-redirection/folder-redirection-rup-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/folder-redirection/folder-redirection-rup-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/folder-redirection/folder-redirection-rup-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: 958888c1-d0e0-bf32-1262-eda1c2185098
---

# Folder Redirection and Roaming User Profiles in Windows and Windows Server | Microsoft Learn

Managing user data and profiles is important for organizations of all sizes. This article explains Folder Redirection and Roaming User Profiles. These features help IT teams centralize data, improve the user experience, and provide easy access to files and settings on different devices.

**Folder Redirection** enables users and administrators to redirect the path of a known folder to a new location, manually or by using Group Policy. The new location can be a folder on the local computer or a directory on a file share. Users interact with files in the redirected folder as if it still existed on the local drive. For example, you can redirect the Documents folder, which is stored on a local drive, to a network location. The files in the folder are then available to the user from any computer on the network.

**Roaming User Profiles** redirects user profiles to a file share so that users receive the same operating system and application settings on multiple computers. When a user signs in to a computer by using an account set up with a file share as the profile path, the user's profile loads to the local computer and merges with the local profile, if present. When the user signs out of the computer, the local copy of their profile merges with the server copy. This process includes any changes made during the session. Typically, a network administrator enables Roaming User Profiles on domain accounts.

## Benefits of Folder Redirection, Offline Files, and Roaming User Profiles

Administrators can use Folder Redirection, Offline Files, and Roaming User Profiles to centralize storage for user data and settings. These features let users access their data while offline or during a network or server outage. These features can also accomplish these specific applications:

- Centralize data from client computers for administrative tasks, such as using a server-based backup tool to back up user folders and settings.
- Enable users to continue accessing network files, even if there's a network or server outage.
- Optimize bandwidth usage and enhance the experience of users in branch offices who access files and folders that are hosted on corporate servers located offsite.
- Enable mobile users to access network files while working offline or over slow networks.

## Primary computers for Folder Redirection and Roaming User Profiles

Primary computers enable you to limit the use of Folder Redirection, Roaming User Profiles, or both to only a user's primary computers.

You can designate a set of computers, known as primary computers, for each domain user, which enables you to control which computers use Folder Redirection, Roaming User Profiles, or both. Designating primary computers is a straightforward way to link user data and settings to specific devices. It makes administration easier, improves data security, and reduces the risk of profile corruption.

There are four major benefits to designating primary computers for users:

- The administrator can specify which computers users can use to access their redirected data and settings. For example, the administrator can configure user data and settings to roam only between specific devices, such as a desktop and a laptop. Meaning the data doesn't roam to other computers, like a shared conference room computer. This approach provides better control and security for user information.
- Designating primary computers reduces the security and privacy risk of leaving residual personal or corporate data on computers where the user has signed in. For example, a general manager who signs in to an employee's computer for temporary access doesn't leave behind any personal or corporate data.
- Primary computers enable the administrator to mitigate the risk of an improperly configured or otherwise corrupt profile, which could result from roaming between differently configured systems, such as between x86-based and x64-based computers.
- The first sign-in on a nonprimary computer, such as a server, is faster because the user's roaming profile and redirected folders aren't downloaded. Sign out times are also reduced, because changes to the user profile don't need to be uploaded to the file share.

### Primary computer behavior

To limit downloading private user data to primary computers, the Folder Redirection and Roaming User Profiles technologies perform the following logic checks when a user signs in to a computer:

- The Windows operating system checks the Group Policy settings (**Download roaming profiles on primary computers only** and **Redirect folders on primary computers only**) to determine if the **msDS-Primary-Computer** attribute in Active Directory Domain Services (AD DS) should influence the decision to roam the user's profile or apply Folder Redirection.
- If the policy setting enables primary computer support, Windows verifies that the AD DS schema supports the **msDS-Primary-Computer** attribute. If it does, Windows determines if the computer that the user is logging on to is designated as a primary computer for the user as follows:

    - If the computer is one of the user's primary computers, Windows uses the Roaming User Profiles and Folder Redirection settings.
    - If the computer isn't a primary computer, Windows does the following:

        - Loads the user's cached local profile, if one exists. If not, it creates a new local profile.
        - Removes any redirected folders based on the removal action set in the previous Group Policy. This action is stored in the local Folder Redirection settings.

For more information, see [Deploy primary computers for Folder Redirection and Roaming User Profiles](deploy-primary-computers)