---
layout: Conceptual
title: rename | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/rename
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Learn how to use the rename command to rename files or directories from the command line in Windows Server, including wildcard examples for batch renaming.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 3dffdafe-c47c-fca1-d46e-eaea65e50ece
document_version_independent_id: 1847815e-969c-dec5-2683-3d2d2f188a53
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/rename.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/rename
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/rename.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: 5f798d89-a3c8-bca5-e375-3b88eebe51ca
---

# rename | Microsoft Learn

Renames one or more files or directories. Use wildcard characters (`*` and `?`) to rename multiple files in a single command.

Note

This command is the same as the [ren command](ren).

## Syntax

```syntax
rename [<drive>:][<path>]<filename1> <filename2>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<drive>:][<path>]<filename1>` | Specifies the location and name of the file or set of files you want to rename. *Filename1* can include wildcard characters (**\*** and **?**). |
| `<filename2>` | Specifies the new name for the file. Use wildcard characters to specify new names for multiple files. |
| `/?` | Shows help at the command prompt. |

#### Remarks

- You can't specify a new drive or path when renaming files. You also can't use this command to rename files across drives or to move files to a different directory.
- Wildcard characters in *filename2* represent the corresponding characters in *filename1*.
- *Filename2* must be a unique file name. If *filename2* matches an existing file name, the following message appears: `Duplicate file name or file not found`.

### Examples

To change all the .txt file name extensions in the current directory to .doc extensions, type:

```cmd
rename *.txt *.doc
```

When you use wildcards in *filename2*, the command replaces each wildcard with the characters in the *same position* in the original name. A **?** keeps the single character in that position, and a **\*** keeps all remaining characters from that position to the end of the name or extension. Because the match is positional, the results can be surprising.

To replace a fixed-length prefix in a set of file names while keeping the rest of each name, type:

```cmd
rename img*.jpg pic*.jpg
```

Because `img` and `pic` are both three characters, each **\*** starts at the same position, so only the prefix changes:

| Original file name | New file name |
| --- | --- |
| `img001.jpg` | `pic001.jpg` |
| `img_final.jpg` | `pic_final.jpg` |

Note

The replacement prefix must be the same length as the text it replaces. For example, `rename img*.jpg photo*.jpg` renames `img001.jpg` to `photo1.jpg`, because `photo` is five characters and overwrites the first five characters (`img00`) of the original name.

To change a single character at a known position and keep the rest of the name, type:

```cmd
rename ??-*.log ??_*.log
```

This command matches names whose third character is a hyphen and replaces only that hyphen with an underscore:

| Original file name | New file name |
| --- | --- |
| `ab-server.log` | `ab_server.log` |
| `db-audit.log` | `db_audit.log` |

To append an extension without removing the current one, type:

```cmd
rename *.log *.log.bak
```

The **\*** keeps the original name and extension, and the command appends `.bak` to the end:

| Original file name | New file name |
| --- | --- |
| `server.log` | `server.log.bak` |
| `app.debug.log` | `app.debug.log.bak` |

To change the name of a directory from *Chap10* to *Part10*, type:

```cmd
rename chap10 part10
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ren command](ren)