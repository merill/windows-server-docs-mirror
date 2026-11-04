---
layout: Conceptual
title: create volume raid | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/create-volume-raid
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the create volume raid command, which creates a RAID-5 volume using three or more specified dynamic disks.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b56b5984-588a-f2f7-56cc-de0501110dc6
document_version_independent_id: 2bb55855-e4e4-77d6-7671-9583b2816bad
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/create-volume-raid.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/create-volume-raid
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/create-volume-raid.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1973d8ab-20d4-11dc-a1d2-941e5aa1afd2
---

# create volume raid | Microsoft Learn

Creates a RAID-5 volume using three or more specified dynamic disks. After you create the volume, the focus automatically shifts to the new volume.

## Syntax

```
create volume raid [size=<n>] disk=<n>,<n>,<n>[,<n>,...] [align=<n>] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| size=`<n>` | The amount of disk space, in megabytes (MB), that the volume will occupy on each disk. If no size is given, the largest possible RAID-5 volume will be created. The disk with the smallest available contiguous free space determines the size for the RAID-5 volume and the same amount of space is allocated from each disk. The actual amount of usable disk space in the RAID-5 volume is less than the combined amount of disk space because some of the disk space is required for parity. |
| disk=`<n>,<n>,<n>[,<n>,...]` | The dynamic disks on which to create the RAID-5 volume. You need at least three dynamic disks in order to create a RAID-5 volume. An amount of space equal to `size=<n>` is allocated on each disk. |
| align=`<n>` | Aligns all volume extents to the closest alignment boundary. Typically used with hardware RAID Logical Unit Number (LUN) arrays to improve performance. `<n>` is the number of kilobytes (KB) from the beginning of the disk to the closest alignment boundary. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To create a RAID-5 volume of 1000 megabytes in size, using disks 1, 2 and 3, type:

```
create volume raid size=1000 disk=1,2,3
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [create command](create)