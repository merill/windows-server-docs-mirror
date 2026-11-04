---
layout: Conceptual
title: active | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/active
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the active command, which on basic disks, marks the partition with focus as active.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 223974fe-b7c4-6ff2-73c5-939403da80a8
document_version_independent_id: e9f30af6-812b-b206-1a3c-fe48cb2b58a9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/active.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/active
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/active.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9f81efb8-87b8-a337-ec55-bd01be30ede4
---

# active | Microsoft Learn

On basic disks, marks the partition with focus as active. Only partitions can be marked as active. A partition must be selected for this operation to succeed. Use the **select partition** command to select a partition and shift the focus to it.

Caution

DiskPart only informs the basic input/output system (BIOS) or Extensible Firmware Interface (EFI) that the partition or volume is a valid system partition or system volume, and is capable of containing the operating system startup files. DiskPart does not check the contents of the partition. If you mistakenly mark a partition as active and it does not contain the operating system startup files, your computer might not start.

## Syntax

```
active
```

## Examples

To mark the partition with focus as the active partition, type:

```
active
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select partition command](select-partition)