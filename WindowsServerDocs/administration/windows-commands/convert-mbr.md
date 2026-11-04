---
layout: Conceptual
title: convert mbr | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/convert-mbr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the convert mbr command, which converts an empty basic disk with the GUID Partition Table (GPT) partition style into a basic disk with the master boot record (MBR) partition style.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 51180a16-c519-f962-40f7-42edf5a7b021
document_version_independent_id: 27047791-7171-361c-2981-09a626a64f78
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/convert-mbr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/convert-mbr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/convert-mbr.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 44fc780a-22da-c442-53e7-c50dbd0132a5
---

# convert mbr | Microsoft Learn

Converts an empty basic disk with the GUID Partition Table (GPT) partition style into a basic disk with the master boot record (MBR) partition style. A basic disk must be selected for this operation to succeed. Use the [select disk command](select-disk) to select a basic disk and shift the focus to it.

Important

The disk must be empty to convert it to a basic disk. Back up your data, and then delete all partitions or volumes before converting the disk.

Note

For instructions regarding how to use this command, see [Change a GUID Partition Table Disk into a Master Boot Record Disk](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc725797%28v=ws.11%29).

## Syntax

```
convert mbr [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To convert a basic disc from GPT partition style to MBR partition style, type&gt;:

```
convert mbr
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [convert command](convert)