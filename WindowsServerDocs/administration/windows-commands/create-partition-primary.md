---
layout: Conceptual
title: create partition primary | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/create-partition-primary
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the create partition primary command, which creates a primary partition on the basic disk with focus.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 86c8ba93-ecd4-1f80-75d2-ce3f5c54a1cb
document_version_independent_id: dea4484a-3957-47d5-c5d8-51847a8c52c1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/create-partition-primary.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/create-partition-primary
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/create-partition-primary.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 851187ad-e6fe-2350-3c4d-d7deb514029c
---

# create partition primary | Microsoft Learn

Creates a primary partition on the basic disk with focus. After the partition has been created, the focus automatically shifts to the new partition.

Important

A basic disk must be selected for this operation to succeed. You must use the [select disk](select-disk) command to select a basic disk and shift the focus to it.

## Syntax

```
create partition primary [size=<n>] [offset=<n>] [id={ <byte> | <guid> }] [align=<n>] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| size=`<n>` | Specifies the size of the partition in megabytes (MB). If no size is given, the partition continues until there is no more unallocated space in the current region. |
| offset=`<n>` | The offset in kilobytes (KB), at which the partition is created. If no offset is given, the partition will start at the beginning of the largest disk extent that is large enough to hold it. |
| align=`<n>` | Aligns all partition extents to the closest alignment boundary. Typically used with hardware RAID Logical Unit Number (LUN) arrays to improve performance. `<n>` is the number of kilobytes (KB) from the beginning of the disk to the closest alignment boundary. |
| id={ `<byte>  | <guid>` } | Specifies the partition type. This parameter is intended for original equipment manufacturer (OEM) use only. Any partition type byte or GUID can be specified with this parameter. DiskPart doesn't check the partition type for validity except to ensure that it is a byte in hexadecimal form or a GUID. **Caution:** Creating partitions with this parameter might cause your computer to fail or be unable to start up. Unless you are an OEM or an IT professional experienced with gpt disks, do not create partitions on gpt disks using this parameter. Instead, always use the [create partition efi](create-partition-efi) command to create EFI System partitions, the [create partition msr](create-partition-msr) command to create Microsoft Reserved partitions, and the [create partition primary](create-partition-primary)) command (without the `id={ <byte>  | <guid>` parameter) to create primary partitions on gpt disks.<br>**For master boot record (MBR) disks**, you must specify a partition type byte, in hexadecimal form, for the partition. If this parameter isn't specified, the command creates a partition of type `0x06`, which specifies that a file system isn't installed. Examples include:<br><br>- **LDM data partition:** 0x42<br>- **Recovery partition:** 0x27<br>- **Recognized OEM partition:** 0x12, 0x84, 0xDE, 0xFE, 0xA0<br><br><br>**For GUID partition table (gpt) disks**, you can specify a partition type GUID for the partition that you want to create. Recognized GUIDs include:<br><br>- **EFI system partition:** c12a7328-f81f-11d2-ba4b-00a0c93ec93b<br>- **Microsoft Reserved partition:** e3c9e316-0b5c-4db8-817d-f92df00215ae<br>- **Basic data partition:** ebd0a0a2-b9e5-4433-87c0-68b6b72699c7<br>- **LDM metadata partition (dynamic disk):** 5808c8aa-7e8f-42e0-85d2-e1e90434cfb3<br>- **LDM data partition (dynamic disk):** af9b60a0-1431-4f62-bc68-3311714a69ad<br>- **Recovery partition:** de94bba4-06d1-4d40-a16a-bfd50179d6ac<br>    If this parameter isn't specified for a gpt disk, the command creates a basic data partition. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without the noerr parameter, an error causes DiskPart to exit with an error code. |

## Examples

To create a primary partition of 1000 megabytes in size, type:

```
create partition primary size=1000
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [assign command](assign)
- [create command](create)
- [select disk](select-disk)