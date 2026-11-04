---
layout: Conceptual
title: tree | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tree
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for tree, which displays the directory structure of a path, or of the disk in a drive, graphically.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 0a3647fd-2127-f673-618e-9842d3e8202c
document_version_independent_id: 00e69fb8-23b3-eb08-47fb-adf04f46fbf1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tree.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tree
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tree.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b0558e2e-48be-f167-6867-11bc026561a4
---

# tree | Microsoft Learn

Displays the directory structure of a path or of the disk in a drive graphically. The structure displayed by this command depends upon the parameters that you specify at the command prompt. If you don't specify a drive or path, this command displays the tree structure beginning with the current directory of the current drive.

## Syntax

```
tree [<drive>:][<path>] [/f] [/a]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<drive>:` | Specifies the drive that contains the disk for which you want to display the directory structure. |
| `<path>` | Specifies the directory for which you want to display the directory structure. |
| /f | Displays the names of the files in each directory. |
| /a | Specifies to use text characters instead of graphic characters to show the lines that link subdirectories. |
| /? | Displays help at the command prompt. |

## Examples

To display the names of all the subdirectories on the disk in your current drive, type:

```
tree \
```

To display, one screen at a time, the files in all the directories on drive C, type:

```
tree c:\ /f | more
```

To print a list of all the directories on drive C to a file, type:

```
tree c:\ /f > <driveletter>:\<filepath>\filename.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)