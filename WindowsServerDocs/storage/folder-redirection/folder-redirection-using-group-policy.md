---
layout: Conceptual
title: Configure Folder Redirection with Group Policy on Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/folder-redirection/folder-redirection-using-group-policy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how to configure Folder Redirection with Group Policy in Windows and Windows Server to manage user data efficiently
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-15T00:00:00.0000000Z
locale: en-us
document_id: 50287ea2-ecd9-f75b-1d33-21b12d695154
document_version_independent_id: 50287ea2-ecd9-f75b-1d33-21b12d695154
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/folder-redirection/folder-redirection-using-group-policy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/folder-redirection/folder-redirection-using-group-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/folder-redirection/folder-redirection-using-group-policy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0cb00560-5ef0-848e-3a6d-99d6580ba91f
---

# Configure Folder Redirection with Group Policy on Windows Server | Microsoft Learn

Folder Redirection allows administrators to redirect folder paths to a new location, either locally or on a network share. Using Group Policy, you can configure these locations under **Windows Settings** in the Group Policy Management Console (GPMC). The path is `<Group Policy Object Name>\User Configuration\Policies\Windows Settings\Folder Redirection`.

To learn more about Folder Redirection, see [Folder Redirection, Offline Files, and Roaming User Profiles overview](folder-redirection-rup-overview).

## Which folders can you redirect?

You can use the GPMC to redirect the following folders:

- AppData/Roaming
- Contacts
- Desktop
- Documents
- Downloads
- Favorites
- Links
- Music
- Pictures
- Saved Games
- Searches
- Start Menu
- Videos

## Types of Folder Redirection

You can configure Folder Redirection to either redirect all users' folders to a single location or assign different locations based on users' security group memberships. The following table summarizes the types of folder redirection.

You can choose between the following settings:

- **Basic—Redirect everyone's folder to the same location**. This setting enables you to redirect everyone's folder to the same location and is applied to all users included in the Group Policy Object. For this setting, you have the following options in specifying a target folder location:

    - **Create a folder for each user under the root path**. This option creates a folder in the form `\\server\share\User Account Name\Folder Name`. Each user has a unique path for their redirected folder.
- **Redirect to the following location**. This option uses an explicit path for the redirection location. If an explicit path is used, it can cause multiple users to share the same path for the redirected folder. Consider using environment variables in the path to create a unique path for each user.
- **Redirect to the local user profile location**. This option moves the location of the folder to the local user profile under the **Users** folder.
- **Advanced—Specify locations for various user groups**. This setting enables you to specify redirection behavior for the folder based on the security group memberships for the GPO.
- **Not configured**. This option is the default setting. This setting specifies that policy-based folder redirection was removed for that GPO. All folders are redirected to the local user profile location or remain where they're based on the redirection options selected. No changes are made to the current folder location.

## Prerequisites for Folder Redirection

To configure Folder Redirection using Group Policy, you must meet the following prerequisites:

- An Active Directory Domain Services (AD DS) domain, with client computers joined to the domain. There are no forest or domain functional-level requirements or schema requirements.
- Permission in AD DS to create and link Group Policy Objects (GPOs) in the domain or organizational unit (OU) where the users are located.
- Client computers running Windows or Windows Server.
- A computer with the Group Policy Management Console installed.

## Configuring Folder Redirection

To configure Folder Redirection using Group Policy, follow these steps:

1. Select the **Start** button, type **Group Policy Management**, open **Group Policy Management** from the best match list.
2. In the console tree, expand the domain or organizational unit (OU) where you want to create or edit the GPO.
3. Perform one of the following actions:

    1. To create a new Group Policy Object (GPO) that specifies which users should perform background synchronization on metered networks, right-click the appropriate domain or organizational unit (OU), and then select **Create a GPO in this domain, and link it here**.

    OR

    1. To edit an existing GPO that specifies which users should perform background synchronization on metered networks, right-click the appropriate GPO, and then select **Edit**.
4. In the **Group Policy Management Editor** policy navigation tree, expand **User Configuration &gt; Policies &gt; Windows Settings &gt; Folder Redirection**.
5. Right-click the folder you want to redirect, and then select **Properties**.
6. On the **Target** tab, select the option that you want to use for the redirection target.
7. Select the target location for the folder redirection, as described in Types of Folder Redirection.
8. If necessary, enter the path for the target location. The path can be a local folder or a network share. The path must be in the form `\\server\share\FolderName`.
9. Select **OK** to save the settings.
10. Repeat the steps for each folder that you want to redirect.

To force the GPO to be applied, run the 'gpupdate /force' command on the client computers or wait for the next Group Policy refresh interval.

## Configuring other settings for the redirected folder

In the **Settings** tab in the **Properties** box for a folder, you can enable the following settings.

- **Grant the user exclusive rights**. This setting is enabled by default and is a recommended setting. This setting specifies that the administrator and other users don't have permissions to access this folder.
- **Move the contents of `<FolderName>` to the new location**. This setting moves all the data the user has in the local folder to the shared folder on the network.

Caution

Moving all data can take a large amount of time, depending on the speed of the connection and volume of data. The time to move all data could be significant if both locations are remote. You might also notice a delay when pinning and unpinning files in remote locations, as the file needs to sync between the cache and the file share.
- **Policy Removal**. The following table summarizes the behavior of redirected folders and their contents when the GPO no longer applies, based on your selections for policy removal. The following policy removal options are available in the **Settings** tab, under **Policy Removal**.

| Policy removal option | Selected setting | Result |
| --- | --- | --- |
| Redirect the folder back to the user profile location when policy is removed^1^ | Enabled | - The folder returns to its user profile location.- The contents are copied, not moved, back to the user profile location. - The contents aren't deleted from the redirected location.- The user continues to have access to the contents, but only on the local computer. |
| Leave the folder in the new location when policy is removed | Enabled | - The folder remains at its redirected location.- The contents remain at the redirected location. - The user continues to have access to the contents at the redirected folder. |

^1^ Moving all data back to the user profile can take a large amount of time, depending on the speed of the connection and volume of data. The time to move all data could be significant if both locations are remote. You might also notice a delay when pinning and unpinning files in remote locations, as the file needs to sync between the cache and the file share.

You can also use the GPMC to configure the following Folder Redirection policy settings:

- **Use localized subfolder names when redirecting Start and My Documents**. This policy is located in the following paths: `Computer Configuration\Policies\Administrative Templates\System\Folder Redirection`, or `User Configuration\Policies\Administrative Templates\System\Folder Redirection`.
- **Do not automatically make redirected folders available offline**. This policy is located in the following path: `User Configuration\Policies\Administrative Templates\System\Folder Redirection`.

## Specify the location of folders in a user profile

You can use Group Policy to specify another location (in other words, "redirect" the location) for folders within user profiles. You can redirect folders either to one location for everyone or to different locations based on the security group membership of users. You can also configure other settings for the redirected folder. The settings that you can configure include:

- Granting exclusive user rights to the folder.
- Moving the contents of the folder to the new location.
- Applying redirection policy to earlier Windows operating systems.
- Specifying system behavior if the policy is removed.