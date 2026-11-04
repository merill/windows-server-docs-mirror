---
layout: Conceptual
title: mklink | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/mklink
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the mklink command, which creates a directory or file symbolic or hard link.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 8715a186-098e-b345-2279-688a9d99ad5d
document_version_independent_id: 70faf0b2-4160-8c9c-80f9-fa09f841b6ce
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/mklink.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/mklink
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/mklink.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 95507654-c925-a215-a6eb-2e19121890b1
---

# mklink | Microsoft Learn

Creates a directory or file symbolic or hard link.

## Syntax

```
mklink [[/d] | [/h] | [/j]] <link> <target>
```

### Parameters

| Parameter | Description |
| --- | --- |
| /d | Creates a directory symbolic link. By default, this command creates a file symbolic link. |
| /h | Creates a hard link instead of a symbolic link. |
| /j | Creates a Directory Junction. |
| `<link>` | Specifies the name of the symbolic link being created. |
| `<target>` | Specifies the path (relative or absolute) that the new symbolic link refers to. |
| /? | Displays help at the command prompt. |

### Examples

To create and remove a symbolic link named MyFolder from the root directory to the \Users\User1\Documents directory, and a hard link named Myfile.file to the example.file file located within the directory, type:

```
mklink /d \MyFolder \Users\User1\Documents
mklink /h \MyFile.file \User1\Documents\example.file
rd \MyFolder
del \MyFile.file
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [del command](del)
- [rd command](rd)
- [New-Item in Windows PowerShell](/en-us/powershell/module/microsoft.powershell.management/new-item?view=powershell-6&amp;preserve-view=true)