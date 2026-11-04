---
layout: Conceptual
title: rd | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/rd
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the rd command, which deletes a directory.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: dc6e97b3-2b24-b088-3478-c7d93380f6ac
document_version_independent_id: 868908c8-6734-2b18-6568-08504c314bd3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/rd.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/rd
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/rd.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 01577388-e0f5-6760-9a73-0ec81c697826
---

# rd | Microsoft Learn

Deletes a directory.

The **rd** command can also run from the Windows Recovery Console, using different parameters. For more information, see [Windows Recovery Environment (WinRE)](/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference).

Note

This command is the same as the [rmdir command](rmdir).

## Syntax

```
rd [<drive>:]<path> [/s [/q]]
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
- You can't use the **rd** command to delete the current directory. If you attempt to delete the current directory, the following error message appears:

    `The process can't access the file because it is being used by another process.`

    If you receive this error message, you must change to a different directory (not a subdirectory of the current directory), and then try again.

### Examples

To change to the parent directory so you can safely remove the desired directory, type:

```
cd ..
```

To remove a directory named *test* (and all its subdirectories and files) from the current directory, type:

```
rd /s test
```

To run the previous example in quiet mode, type:

```
rd /s /q test
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)