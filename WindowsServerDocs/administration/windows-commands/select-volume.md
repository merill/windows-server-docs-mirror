---
layout: Conceptual
title: select volume | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/select-volume
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the select volume command, which selects the specified volume and shifts the focus to it.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: fd070a07-e932-20c0-2e6b-5a30a3cb7472
document_version_independent_id: 3859dfef-24f0-fb8e-b4ee-28e0ef0cc471
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/select-volume.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/select-volume
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/select-volume.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 60092074-ba81-63f3-2b2e-93e1064886fd
---

# select volume | Microsoft Learn

Selects the specified volume and shifts the focus to it. This command can also be used to display the volume that currently has the focus in the selected disk.

## Syntax

```
select volume={<n>|<d>}
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<n>` | The number of the volume to receive the focus. You can view the numbers for all volumes on the disk currently selected by using the **list volume** command in DiskPart. |
| `<d> ` | The drive letter or mount point path of the volume to receive the focus. |

## Remarks

- If no volume is specified, this command displays the volume that currently has the focus in the selected disk.
- On a basic disk, selecting a volume also gives the focus to the corresponding partition.

    - If a volume is selected with a corresponding partition, the partition will be automatically selected.
    - If a partition is selected with a corresponding volume, the volume will be automatically selected.

## Examples

To shift the focus to *volume 2*, type:

```
select volume=2
```

To shift the focus to *Drive C*, type:

```
select volume=c
```

To shift the focus to the volume mounted on a folder named *c:\mountpath*, type:

```
select volume=c:\mountpath
```

To display the volume that currently has the focus in the selected disk, type:

```
select volume
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [add volume command](add-volume)
- [attributes volume command](attributes-volume)
- [create volume mirror command](create-volume-mirror)
- [create volume raid command](create-volume-raid)
- [create volume simple command](create-volume-simple)
- [create volume stripe command](create-volume-stripe)
- [delete volume command](delete-volume)
- [detail volume command](detail-volume)
- [fsutil volume command](fsutil-volume)
- [list volume command](list-volume)
- [offline volume command](offline-volume)
- [onine volume command](online-volume)
- [select disk command](select-disk)
- [select partition command](select-partition)
- [select vdisk command](select-vdisk)