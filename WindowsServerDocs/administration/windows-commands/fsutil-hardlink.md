---
layout: Conceptual
title: fsutil hardlink | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-hardlink
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil hardlink command, which creates a hard link between an existing file and a new file.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 00b1f40c-2655-9080-0345-5680d6f213ee
document_version_independent_id: c2f1fdce-3e99-e935-079a-382d62c3645e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-hardlink.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-hardlink
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-hardlink.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d4b74ac8-1a02-fdff-d7cb-6fb0658021e1
---

# fsutil hardlink | Microsoft Learn

Creates a hard link between an existing file and a new file. A hard link is a directory entry for a file. Every file can be considered to have at least one hard link.

On NTFS volumes, each file can have multiple hard links, so a single file can appear in many directories (or even in the same directory with different names). Because all of the links reference the same file, programs can open any of the links and modify the file. A file is deleted from the file system only after all links to it have been deleted. After you create a hard link, programs can use it like any other file name.

## Syntax

```
fsutil hardlink create <newfilename> <existingfilename>
fsutil hardlink list <filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| create | Establishes an NTFS hard link between an existing file and a new file. (An NTFS hard link is similar to a POSIX hard link.) |
| &lt;newfilename&gt; | Specifies the file that you want to create a hard link to. |
| &lt;existingfilename&gt; | Specifies the file that you want to create a hard link from. |
| list | Lists the hard links to *filename*. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)