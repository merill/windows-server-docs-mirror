---
layout: Conceptual
title: edit | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/edit
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the edit command, which starts the MS-DOS Editor, so you can create and change ASCII text files.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 0a33810a-1372-cc85-10df-3f2aad2ae812
document_version_independent_id: 3440fe6d-61d8-3b9a-8316-4db564a2b3da
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/edit.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/edit
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/edit.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: d47cdc65-c993-914d-5f38-605ebfa9dbb5
---

# edit | Microsoft Learn

Starts the MS-DOS Editor, which creates and changes ASCII text files.

## Syntax

```
edit [/b] [/h] [/r] [/s] [/<nnn>] [[<drive>:][<path>]<filename> [<filename2> [...]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<drive>:][<path>]<filename> [<filename2> [...]]` | Specifies the location and name of one or more ASCII text files. If the file doens't exist, MS-DOS Editor creates it. If the file exists, MS-DOS Editor opens it and displays its contents on the screen. The *filename* option can contain wildcard characters (**\*** and **?**). Separate multiple file names with spaces. |
| /b | Forces monochrome mode, so that MS-DOS Editor displays in black and white. |
| /h | Displays the maximum number of lines possible for the current monitor. |
| /r | Loads file(s) in read-only mode. |
| /s | Forces the use of short filenames. |
| `<nnn>` | Loads binary file(s), wrapping lines to *nnn* characters wide. |
| /? | Displays help at the command prompt. |

#### Remarks

- For additional help, open MS-DOS Editor, and then press the F1 key.
- Some monitors don't support the display of shortcut keys by default. If your monitor doesn't display shortcut keys, use **/b**.

### Examples

To open MS-DOS Editor, type:

```
edit
```

To create and modify a file named *newtextfile.txt* in the current directory, type:

```
edit newtextfile.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)