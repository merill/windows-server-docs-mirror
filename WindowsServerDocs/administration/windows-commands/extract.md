---
layout: Conceptual
title: extract | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/extract
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the extract command, which extracts files from a source location.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-12-29T00:00:00.0000000Z
locale: en-us
document_id: db77b414-495f-226e-2113-c3190795b6e0
document_version_independent_id: 2674c563-9861-8dde-cb73-a3fbe5995c3a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/extract.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/extract
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/extract.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 8b267efe-dfb6-7d51-5dc4-5920421a193c
---

# extract | Microsoft Learn

Extracts files from a cabinet or source.

Note

On Windows Server 2016 and newer, and on Windows 10, the program file Extract.exe is neither provided nor supported. It is replaced by Extrac32.exe, originally part of Internet Explorer, now part of the operating system.

## Syntax

## Extract.exe

```
extract [/y] [/a] [/d | /e] [/l dir] cabinet [filename ...]
extract [/y] source [newname]
extract [/y] /c source destination
```

### Parameters

| Parameter | Description |
| --- | --- |
| cabinet | Use if you want to extract two or more files. |
| filename | Name of the file to extract from the cabinet. Wild cards and multiple filenames (separated by blanks) may be used. |
| source | Compressed file (a cabinet with only one file). |
| newname | New filename to give the extracted file. If not supplied, the original name is used. |
| /a | Process ALL cabinets. Follows cabinet chain starting in first cabinet mentioned. |
| /c | Copy source file to destination (to copy from DMF disks). |
| /d | Display cabinet directory (use with filename to avoid extract). |
| /e | Extract (use instead of *.* to extract all files). |
| /l dir | Location to place extracted files (default is current directory). |
| /y | Don't prompt before overwriting an existing file. |

## Extrac32.exe

Note

Extrac32.exe can be used from the command line, but does not display any output on the console. Redirect the help output through the [more](more) command, like this: `extrac32.exe /? | more`

```
Extrac32 [/Y] [/A] [/D | /E] [/L dir] cabinet [filename ...]
Extrac32 [/Y] source [newname]
Extrac32 [/Y] /C source destination
```

### Parameters

| Parameter | Description |
| --- | --- |
| cabinet | Cabinet file (contains two or more files). |
| filename | Name of the file to extract from the cabinet. Wild cards and multiple filenames (separated by blanks) may be used. |
| source | Compressed file (a cabinet with only one file). |
| newname | New filename to give the extracted file. If not supplied, the original name is used. |
| /A | Process ALL cabinets. Follows cabinet chain starting in first cabinet mentioned. |
| /C | Copy source file to destination (to copy from DMF disks). |
| /D | Display cabinet directory (use with filename to avoid extract). |
| /E | Extract (use instead of *.* to extract all files). |
| /L dir | Location to place extracted files (default is current directory). |
| /Y | Do not prompt before overwriting an existing file. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)