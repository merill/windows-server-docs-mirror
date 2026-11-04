---
layout: Conceptual
title: select partition | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/select-partition
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the select partition command, which selects the specified partition and shifts the focus to it.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4e9009f9-a76a-e1fa-26fa-7043dfb24e01
document_version_independent_id: 6fa881f4-e818-f513-50db-1ab192a5241b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/select-partition.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/select-partition
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/select-partition.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2e19130a-76d9-a156-e743-71ff9a4484e6
---

# select partition | Microsoft Learn

Selects the specified partition and shifts the focus to it. This command can also be used to display the partition that currently has the focus in the selected disk.

## Syntax

```
select partition=<n>
```

### Parameters

| Parameter | Description |
| --- | --- |
| partition=`<n>` | The number of the partition to receive the focus. You can view the numbers for all partitions on the disk currently selected by using the **list partition** command in DiskPart. |

#### Remarks

- Before you can select a partition you must first select a disk using the **select disk** command.

    - If no partition number is specified, this option displays the partition that currently has the focus in the selected disk.
    - If a volume is selected with a corresponding partition, the partition is automatically selected.
    - If a partition is selected with a corresponding volume, the volume is automatically selected.

## Examples

To shift the focus to *partition 3*, type:

```
select partitition=3
```

To display the partition that currently has the focus in the selected disk, type:

```
select partition
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [create partition efi command](create-partition-efi)
- [create partition extended command](create-partition-extended)
- [create partition logical command](create-partition-logical)
- [create partition msr command](create-partition-msr)
- [create partition primary command](create-partition-primary)
- [delete partition command](delete-partition)
- [detail partition command](detail-partition)
- [select disk command](select-disk)
- [select vdisk command](select-vdisk)
- [select volume command](select-volume)