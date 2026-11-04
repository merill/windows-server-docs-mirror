---
layout: Conceptual
title: select commands | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/select
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the select commands, which shifts the focus to a disk, partition, volume, or virtual hard disk (VHD).
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 03f0f613-647d-f3d7-e13f-35e20d4d034e
document_version_independent_id: f65b409d-2800-40f7-dea8-40b3cf5ca36d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/select.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/select
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/select.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cc3c3da6-241f-ff06-d848-43135faef8c7
---

# select commands | Microsoft Learn

Shifts the focus to a disk, partition, volume, or virtual hard disk (VHD).

## Syntax

```
select disk
select partition
select vdisk
select volume
```

### Parameters

| Parameter | Description |
| --- | --- |
| [Select disk](select-disk) | Shifts the focus to a disk. |
| [Select partition](select-partition) | Shifts the focus to a partition. |
| [Select vdisk](select-vdisk) | Shifts the focus to a VHD. |
| [Select volume](select-volume) | Shifts the focus to a volume. |

#### Remarks

- If a volume is selected with a corresponding partition, the partition will be automatically selected.
- If a partition is selected with a corresponding volume, the volume will be automatically selected.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)