---
layout: Conceptual
title: ren | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ren
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ren command, which renames a file or directory.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: 54d66847-a721-6cca-98c5-8e52499686af
document_version_independent_id: 87f1e6a4-dafa-11a8-ea95-806a33f65e4b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ren.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ren
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ren.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9f73e2ed-dd21-54eb-cb0f-833d5d82b572
---

# ren | Microsoft Learn

Renames files or directories.

Note

This command is the same as the [rename command](rename).

## Syntax

```
ren [<drive>:][<path>]<filename1> <filename2>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<drive>:][<path>]<filename1>` | Specifies the location and name of the file or set of files you want to rename. *Filename1* can include wildcard characters (**\*** and **?**). |
| `<filename2>` | Specifies the new name for the file. You can use wildcard characters to specify new names for multiple files. |
| /? | Displays help at the command prompt. |

#### Remarks

- You can't specify a new drive or path when renaming files. You also can't use this command to rename files across drives or to move files to a different directory.
- Characters represented by wildcard characters in *filename2* will be identical to the corresponding characters in *filename1*.
- *Filename2* must be a unique file name. If *filename2* matches an existing file name, the following message appears: `Duplicate file name or file not found`.

### Examples

To change all the .txt file name extensions in the current directory to .doc extensions, type:

```
ren *.txt *.doc
```

To change the name of a directory from *Chap10* to *Part10*, type:

```
ren chap10 part10
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [rename command](rename)