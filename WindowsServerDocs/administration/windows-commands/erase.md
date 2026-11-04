---
layout: Conceptual
title: erase | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/erase
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the erase command, which deletes one or more files.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: dbb6956b-5897-1c44-e029-e9a6fe89c28c
document_version_independent_id: 66fc89c8-a34d-c9df-6fab-c02b73607375
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/erase.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/erase
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/erase.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 522b22cc-5d88-fdf4-e59b-dc9db4a37187
---

# erase | Microsoft Learn

Deletes one or more files. If you use **erase** to delete a file from your disk, you can't retrieve it.

Note

This command is the same as the [del command](del).

## Syntax

```
erase [/p] [/f] [/s] [/q] [/a[:]<attributes>] <names>
del [/p] [/f] [/s] [/q] [/a[:]<attributes>] <names>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<names>` | Specifies a list of one or more files or directories. Wildcards may be used to delete multiple files. If a directory is specified, all files within the directory will be deleted. |
| /p | Prompts for confirmation before deleting the specified file. |
| /f | Forces deletion of read-only files. |
| /s | Deletes specified files from the current directory and all subdirectories. Displays the names of the files as they are being deleted. |
| /q | Specifies quiet mode. You are not prompted for delete confirmation. |
| /a[:]`<attributes>` | Deletes files based on the following file attributes:<br>- **r** Read-only files<br>- **h** Hidden files<br>- **i** Not content indexed files<br>- **s** System files<br>- **a** Files ready for archiving<br>- **l** Reparse points<br>- **-** Used as a prefix meaning 'not' |
| /? | Displays help at the command prompt. |

#### Remarks

- If you use the `erase /p` command, you'll see the following message:

    `FileName, Delete (Y/N)?`

    To confirm the deletion, press **Y**. To cancel the deletion and to display the next file name (if you specified a group of files), press **N**. To stop the **erase** command, press CTRL+C.
- If you disable command extension, the **/s** parameter will display the names of any files that weren't found ,instead of displaying the names of files that are being deleted.
- If you specify specific folders in the `<names>` parameter, all of the included files will also be deleted. For example, if you want to delete all of the files in the *\work* folder, type:

    ```
    erase \work
    ```
- You can use wildcards (**\*** and **?**) to delete more than one file at a time. However, to avoid deleting files unintentionally, you should use wildcards cautiously. For example, if you type the following command:

    ```
    erase *.*
    ```

    The **erase** command displays the following prompt:

    `Are you sure (Y/N)?`

    To delete all of the files in the current directory, press **Y** and then press ENTER. To cancel the deletion, press **N** and then press ENTER.

    Note

    Before you use wildcard characters with the **erase** command, use the same wildcard characters with the **dir** command to list all the files that will be deleted.

### Examples

To delete all the files in a folder named Test on drive C, type either of the following:

```
erase c:\test
erase c:\test\*.*
```

To delete all files with the .bat file name extension from the current directory, type:

```
erase *.bat
```

To delete all read-only files in the current directory, type:

```
erase /a:r *.*
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [del command](del)