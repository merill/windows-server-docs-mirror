---
layout: Conceptual
title: rmdir | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/rmdir
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the rmdir command, which deletes a directory.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 662e241e-a625-cae7-7ce5-604ee3c7f64a
document_version_independent_id: 01dd3ff4-64fa-42d6-ed54-2fcef0168403
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/rmdir.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/rmdir
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/rmdir.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 874d3bc6-e0ee-bcc2-3e11-690f78648289
---

# rmdir | Microsoft Learn

Deletes a directory.

The **rmdir** command can also run from the Windows Recovery Console, using different parameters. For more information, see [Windows Recovery Environment (WinRE)](/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference).

Note

This command is the same as the [rd command](rd).

## Syntax

```
rmdir [<drive>:]<path> [/s [/q]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<drive>:]<path>` | Specifies the location and the name of the directory that you want to delete. *Path* is required. If you include a backslash () at the beginning of the specified *path*, then the *path* starts at the root directory (regardless of the current directory). |
| /s | Deletes a directory tree (the specified directory and all its subdirectories, including all files). |
| /q | Specifies quiet mode. Does not prompt for confirmation when deleting a directory tree. The **/q** parameter works only if **/s** is also specified.<br>**CAUTION:** When you run in quiet mode, the entire directory tree is deleted without confirmation. Make sure that important files are moved or backed up before using the **/q** command-line option. |
| /? | Displays help at the command prompt. |

#### Remarks

- You can't delete a directory that contains files, including hidden or system files. If you attempt to do so, the following message appears:

    `The directory is not empty`

    Use the **dir /a** command to list all files (including hidden and system files). Then use the **attrib** command with **-h** to remove hidden file attributes, **-s** to remove system file attributes, or **-h -s** to remove both hidden and system file attributes. After the hidden and file attributes have been removed, you can delete the files.
- You can't use the **rmdir** command to delete the current directory. If you attempt to delete the current directory, the following error message appears:

    `The process can't access the file because it is being used by another process.`

    If you receive this error message, you must change to a different directory (not a subdirectory of the current directory), and then try again.

## Examples

To change to the parent directory so you can safely remove the desired directory, type:

```
cd ..
```

To remove a directory named *test* (and all its subdirectories and files) from the current directory, type:

```
rmdir /s test
```

To run the previous example in quiet mode, type:

```
rmdir /s /q test
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)