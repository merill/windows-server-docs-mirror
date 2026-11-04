---
layout: Conceptual
title: create partition extended | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/create-partition-extended
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the create partition extended command, which creates an extended partition on the disk with focus.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9d59abb0-45c3-ca4f-290e-24e37ada026a
document_version_independent_id: bd213a53-4a30-4d5e-b532-6d8114327d19
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/create-partition-extended.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/create-partition-extended
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/create-partition-extended.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: aeac5f57-f59b-6d4b-64ec-4ef8c1f0a30c
---

# create partition extended | Microsoft Learn

Creates an extended partition on the disk with focus. After the partition has been created, the focus automatically shifts to the new partition.

Important

You can use this command only on Master Boot Record (MBR) disks. You must use the [select disk](select-disk) command to select a basic MBR disk and shift the focus to it.

You must create an extended partition before you can create logical drives. Only one extended partition can be created per disk. This command fails if you attempt to create an extended partition within another extended partition.

## Syntax

```
create partition extended [size=<n>] [offset=<n>] [align=<n>] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| size=`<n>` | Specifies the size of the partition in megabytes (MB). If no size is given, the partition continues until there is no more free space in the extended partition. |
| offset=`<n>` | Specifies the offset in kilobytes (KB), at which the partition is created. If no offset is given, the partition will start at the beginning of the free space on the disk that is large enough to hold the new partition. |
| align=`<n>` | Aligns all partition extents to the closest alignment boundary. Typically used with hardware RAID Logical Unit Number (LUN) arrays to improve performance. `<n>` is the number of kilobytes (KB) from the beginning of the disk to the closest alignment boundary. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To create an extended partition of 1000 megabytes in size, type:

```
create partition extended size=1000
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [create command](create)
- [select disk](select-disk)