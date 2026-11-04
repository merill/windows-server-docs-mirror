---
layout: Conceptual
title: fsutil wim | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-wim
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil wim command, which provides functions to discover and manage Windows Image (WIM)-backed files.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 576ae59e-af0a-b10f-b710-bbe05270fc1c
document_version_independent_id: 28ff7133-e173-6bd8-3a15-70ce0e002645
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-wim.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-wim
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-wim.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: bdf14d34-364c-dd52-2eb6-55458279c206
---

# fsutil wim | Microsoft Learn

Provides functions to discover and manage Windows Image (WIM)-backed files.

## Syntax

```
fsutil wim [enumfiles] <drive name> <data source>
fsutil wim [enumwims] <drive name>
fsutil wim [queryfile] <filename>
fsutil wim [removewim] <drive name> <data source>
```

### Parameters

| Parameter | Description |
| --- | --- |
| enumfiles | Enumerates WIM backed files. |
| `<drive name>` | Specifies the drive name. |
| `<data source>` | Specifies the data source. |
| enumwims | Enumerates backing WIM files. |
| queryfile | Queries if the file is backed by WIM, and if so, displays details about the WIM file. |
| `<filename>` | Specifies the filename. |
| removewim | Removes a WIM from backing files. |

### Examples

To enumerate the files for drive C: from data source 0, type:

```
fsutil wim enumfiles C: 0
```

To enumerate backing WIM files for drive C:, type:

```
fsutil wim enumwims C:
```

To see if a file is backed by WIM, type:

```
fsutil wim queryFile C:\Windows\Notepad.exe
```

To remove the WIM from backing files for volume C: and data source 2, type:

```
fsutil wim removewims C: 2
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)