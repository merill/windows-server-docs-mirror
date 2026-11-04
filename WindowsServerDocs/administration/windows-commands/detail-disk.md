---
layout: Conceptual
title: detail disk | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/detail-disk
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the detail disk command, which displays the properties of the selected disk and the volumes on that disk.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 0746e2df-8460-4339-8390-2340bbb95648
document_version_independent_id: 2024f23f-c6c7-b146-3241-eda36b17ee7b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/detail-disk.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/detail-disk
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/detail-disk.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f0cff53f-8037-a22a-55be-1d835a6153a1
---

# detail disk | Microsoft Learn

Displays the properties of the selected disk and the volumes on that disk. Before you begin, you must select a disk for this operation to succeed. Use the [select disk](select-disk) command to select a disk and shift the focus to it. If you select a virtual hard disk (VHD), this command will show the disk's bus type as *Virtual*.

## Syntax

```
detail disk
```

## Examples

To see the properties of the selected disk, and information about the volumes in the disk, type:

```
detail disk
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [detail command](detail)