---
layout: Conceptual
title: bdehdcfg target | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bdehdcfg-target
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bdehdcfg target command, which prepares a partition for use as a system drive by BitLocker and Windows recovery.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ae514b57-1447-df86-6d59-82f5977e979d
document_version_independent_id: ccd39e47-f540-08d7-d85c-f2b0af24a2cb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bdehdcfg-target.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bdehdcfg-target
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bdehdcfg-target.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 5ec6cfa4-8de8-c2f8-b1bb-2387428c9a48
---

# bdehdcfg target | Microsoft Learn

Prepares a partition for use as a system drive by BitLocker and Windows Recovery. By default, this partition is created without a drive letter.

## Syntax

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge}
```

#### Parameters

| Parameter | Description |
| --- | --- |
| default | Indicates that the command-line tool will follow the same process as the BitLocker setup wizard. |
| unallocated | Creates the system partition out of the unallocated space available on the disk. |
| `<drive_letter>` shrink | Reduces the drive specified by the amount necessary to create an active system partition. To use this command, the drive specified must have at least 5 percent free space. |
| `<drive_letter>` merge | Uses the drive specified as the active system partition. The operating system drive cannot be a target for merge. |

## Examples

To designate an existing drive (P) as the system drive:

```
bdehdcfg -target P: merge
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bdehdcfg](bdehdcfg)