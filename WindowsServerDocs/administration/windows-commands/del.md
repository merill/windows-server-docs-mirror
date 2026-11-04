---
layout: Conceptual
title: del | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/del
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the del command, which deletes one or more files.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-06-22T00:00:00.0000000Z
locale: en-us
document_id: e809f83e-26b1-52b5-a663-e2d3705e7cdc
document_version_independent_id: b968d3d3-1ba0-65a8-524e-3c5e4118209f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/del.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/del
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/del.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7d0c907a-8de0-24c9-3279-0a4c515f6a80
---

# del | Microsoft Learn

Deletes one or more files. This command performs the same actions as the **erase** command.

The **del** command can also run from the Windows Recovery Console, using different parameters. For more information, see [Windows Recovery Environment (WinRE)](/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference).

Warning

If you use **del** to delete a file from your disk, you can't retrieve it.

## Syntax

```
del [/p] [/f] [/s] [/q] [/a[:]<attributes>] <names>
erase [/p] [/f] [/s] [/q] [/a[:]<attributes>] <names>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<names>` | Specifies a list of one or more files or directories. Wildcards may be used to delete multiple files. If a directory is specified, all files within the directory will be deleted. |
| /p | Prompts for confirmation before deleting the specified file. |
| /f | Forces deletion of read-only files. |
| /s | Deletes specified files from the current directory and all subdirectories. Displays the names of the files as they are being deleted. |
| /q | Specifies quiet mode. You are not prompted for delete confirmation. |
| /a[:]`<attributes>` | Deletes files based on the following file attributes:<br>- **r** Read-only files<br>- **h** Hidden files<br>- **i** Not content indexed files<br>- **s** System files<br>- **a** Files ready for archiving<br>- **l** Reparse points<br>- **-** Used as a prefix meaning 'not'<br><br>. |
| /? | Displays help at the command prompt. |

#### Remarks

- If you use the `del /p` command, you'll see the following message:

    `FileName, Delete (Y/N)?`

    To confirm the deletion, press **Y**. To cancel the deletion and to display the next file name (if you specified a group of files), press **N**. To stop the **del** command, press CTRL+C.
- If you disable command extension, the **/s** parameter will display the names of any files that weren't found ,instead of displaying the names of files that are being deleted.
- If you specify specific folders in the `<names>` parameter, all of the included files will also be deleted. For example, if you want to delete all of the files in the *\work* folder, type:

    ```
    del \work
    ```
- You can use wildcards (**\*** and **?**) to delete more than one file at a time. However, to avoid deleting files unintentionally, you should use wildcards cautiously. For example, if you type the following command:

    ```
    del *.*
    ```

    The **del** command displays the following prompt:

    `Are you sure (Y/N)?`

    To delete all of the files in the current directory, press **Y** and then press ENTER. To cancel the deletion, press **N** and then press ENTER.

    Note

    Before you use wildcard characters with the **del** command, use the same wildcard characters with the **dir** command to list all the files that will be deleted.

## Examples

To delete all the files in a folder named Test on drive C, type either of the following:

```
del c:\test
del c:\test\*.*
```

To delete all the files in a folder where the folder has a space in its name, the full path needs to be wrapped in double quotes. Type either of the following:

```
del "c:\test folder\"
del "c:\test folder\*.*"
```

To delete all files with the .bat file name extension from the current directory, type:

```
del *.bat
```

To delete all read-only files in the current directory, type:

```
del /a:r *.*
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Windows Recovery Environment (WinRE)](/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)