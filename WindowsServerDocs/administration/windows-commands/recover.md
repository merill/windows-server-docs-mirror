---
layout: Conceptual
title: recover | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/recover
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the recover command, which recovers readable information from a bad or defective disk.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 3740c687-1762-9dbd-03e7-739643dfda44
document_version_independent_id: 7de9f827-94e5-38aa-2d8b-8cc297bfdb22
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/recover.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/recover
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/recover.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 61107cbc-6cbd-04f4-e48a-0623ff0bbc3a
---

# recover | Microsoft Learn

Recovers readable information from a bad or defective disk. This command reads a file, sector-by-sector, and recovers data from the good sectors. Data in bad sectors is lost. Because all data in bad sectors is lost when you recover a file, you should recover only one file at a time.

Bad sectors reported by the **chkdsk** command were marked as bad when your disk was prepared for operation. They pose no danger, and **recover** does not affect them.

## Syntax

```
recover [<drive>:][<path>]<filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<drive>:][<path>]<filename>` | Specifies the file name (and the location of the file if it is not in the current directory) you want to recover. *Filename* is required and wildcards aren't supported. |
| /? | Displays help at the command prompt. |

### Examples

To recover the file *story.txt* in the *\fiction* directory on drive D, type:

```
recover d:\fiction\story.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)