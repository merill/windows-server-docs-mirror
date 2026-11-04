---
layout: Conceptual
title: change user | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/change-user
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the change user command, which changes the install mode for the Remote Desktop Session Host server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 392976e6-f5f1-701b-51af-607b1a85e62e
document_version_independent_id: 6fbc5e70-afe0-8d87-8ca1-3b68b7375ac5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/change-user.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/change-user
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/change-user.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: cff942c7-6a83-1696-c020-c4375b7b5f69
---

# change user | Microsoft Learn

Changes the install mode for the Remote Desktop Session Host server.

Note

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
change user {/execute | /install | /query}
```

### Parameters

| Parameter | Description |
| --- | --- |
| /execute | Enables .ini file mapping to the home directory. This is the default setting. |
| /install | Disables .ini file mapping to the home directory. All .ini files are read and written to the system directory. You must disable .ini file mapping when installing applications on a Remote Desktop Session Host server. |
| /query | Displays the current setting for .ini file mapping. |
| /? | Displays help at the command prompt. |

#### Remarks

- Use **change user /install** before installing an application to create .ini files for the application in the system directory. These files are used as the source when user-specific .ini files are created. After installing the application, use **change user /execute** to revert to standard .ini file mapping.
- The first time you run the app, it searches the home directory for its .ini files. If the .ini files aren't found in the home directory, but are found in the system directory, Remote Desktop Services copies the .ini files to the home directory, ensuring that each user has a unique copy of the application .ini files. Any new .ini files are created in the home directory.
- Each user should have a unique copy of the .ini files for an application. This prevents instances where different users might have incompatible application configurations (for example, different default directories or screen resolutions).
- When the system is running **change user /install**, several things occur. All registry entries that are created are shadowed under **HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows NT\Currentversion\Terminal Server\Install**, in either the **\SOFTWARE** subkey or the **\MACHINE** subkey. Subkeys added to **HKEY\_CURRENT\_USER** are copied under the **\SOFTWARE** subkey, and subkeys added to **HKEY\_LOCAL\_MACHINE** are copied under the **\MACHINE** subkey. If the application queries the Windows directory by using system calls, such as GetWindowsdirectory, the rd Session Host server returns the systemroot directory. If any .ini file entries are added by using system calls, such as WritePrivateProfileString, they are added to the .ini files under the systemroot directory.
- When the system returns to **change user /execute**, and the application tries to read a registry entry under **HKEY\_CURRENT\_USER** that does not exist, Remote Desktop Services checks to see whether a copy of the key exists under the **\Terminal Server\Install** subkey. If it does, the subkeys are copied to the appropriate location under **HKEY\_CURRENT\_USER**. If the application tries to read from an .ini file that does not exist, Remote Desktop Services searches for that .ini file under the system root. If the .ini file is in the system root, it is copied to the \Windows subdirectory of the user's home directory. If the application queries the Windows directory, the rd Session Host server returns the \Windows subdirectory of the user's home directory.
- When you log on, Remote Desktop Services checks whether its system .ini files are newer than the .ini files on your computer. If the system version is newer, your .ini file is either replaced or merged with the newer version. This depends on whether or not the INISYNC bit, 0x40, is set for this .ini file. Your previous version of the .ini file is renamed as Inifile.ctx. If the system registry values under the **\Terminal Server\Install** subkey are newer than your version under **HKEY\_CURRENT\_USER**, your version of the subkeys is deleted and replaced with the new subkeys from **\Terminal Server\Install**.

## Examples

- To disable .ini file mapping in the home directory, type:

    ```
    change user /install
    ```
- To enable .ini file mapping in the home directory, type:

    ```
    change user /execute
    ```
- To display the current setting for .ini file mapping, type:

    ```
    change user /query
    ```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [change command](change)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)