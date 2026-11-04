---
layout: Conceptual
title: takeown | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/takeown
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the takeown command, which enables an administrator to recover access to a file that was previously denied.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-11-04T00:00:00.0000000Z
locale: en-us
document_id: dc00bc99-0b73-9ffd-f3bb-64569079dbcb
document_version_independent_id: a8aadbc5-1ea3-71e6-7989-25daf422636d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/takeown.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/takeown
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/takeown.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: 5af29ab2-adfe-7ff1-4206-1ebc37979bc8
---

# takeown | Microsoft Learn

Enables an administrator to recover access to a file that previously was denied, by making the administrator the owner of the file. This command is typically used on batch files.

## Syntax

```
takeown [/s <computer> [/u [<domain>\]<username> [/p [<password>]]]] /f <filename> [/a] [/r [/d {Y|N}]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /s `<computer>` | Specifies the name or IP address of a remote computer (do not use backslashes). The default value is the local computer. This parameter applies to all of the files and folders specified in the command. |
| /u `[<domain>\]<username>` | Runs the script with the permissions of the specified user account. The default value is system permissions. |
| /p `[<[password>]` | Specifies the password of the user account that is specified in the **/u** parameter. |
| /f `<filename>` | Specifies the file name or directory name pattern. You can use the wildcard character `*` when specifying the pattern. You can also use the syntax `<sharename>\<filename>`. |
| /a | Gives ownership to the Administrators group instead of the current user. If you don't specify this option, file ownership is given to the user who is currently logged on to the computer. |
| /r | Performs a recursive operation on all files in the specified directory and subdirectories. |
| /d `{Y | N}` | Suppresses the confirmation prompt that is displayed when the current user does not have the **List Folder** and **Read** permissions on a specified directory, and instead uses the specified default value. Valid values for the **/d** option are:<br>- **Y** - Take ownership of the directory. The directory permissions are replaced with permission granting the user full control only.<br>- **N** - Skip the directory.<br>    **NOTE**You must use this option in conjunction with the **/r** option. |
| /? | Displays help at the command prompt. |

## Remarks

- Mixed patterns using (**?** and **\***) aren't supported by **takeown** command.
- After deleting the lock with **takeown**, you might have to use Windows Explorer to give yourself full permissions to the files and directories before you can delete them.

## Examples

To take ownership of a file named *Lostfile*, type:

```
takeown /f lostfile
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)