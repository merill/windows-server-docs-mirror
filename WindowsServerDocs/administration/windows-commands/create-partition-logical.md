---
layout: Conceptual
title: create partition logical | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/create-partition-logical
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the create partition logical command, which creates a logical partition in an existing extended partition.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: cc96f35b-8a8e-7d64-0978-90b3eaaaea7c
document_version_independent_id: 676e4582-fc96-927f-cf8a-b20ad9f50319
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/create-partition-logical.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/create-partition-logical
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/create-partition-logical.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae4557f9-4267-5f42-eda8-8251511f7b0a
---

# create partition logical | Microsoft Learn

Creates a logical partition on an existing extended partition. After the partition has been created, the focus automatically shifts to the new partition.

Important

You can use this command only on Master Boot Record (MBR) disks. You must use the [select disk](select-disk) command to select a basic MBR disk and shift the focus to it.

You must create an [extended partition](create-partition-extended) before you can create logical drives.

## Syntax

```
create partition logical [size=<n>] [offset=<n>] [align=<n>] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| size=`<n>` | Specifies the size of the logical partition in megabytes (MB), which must be smaller than the extended partition. If no size is given, the partition continues until there is no more free space in the extended partition. |
| offset=`<n>` | Specifies the offset in kilobytes (KB), at which the partition is created. The offset rounds up to completely fill whatever cylinder size is used. If no offset is given, then the partition is placed in the first disk extent that is large enough to hold it. The partition is at least as long in bytes as the number specified by **size=`<n>`**. If you specify a size for the logical partition, it must be smaller than the extended partition. |
| align=`<n>` | Aligns all volume or partition extents to the closest alignment boundary. Typically used with hardware RAID Logical Unit Number (LUN) arrays to improve performance. `<n>` is the number of kilobytes (KB) from the beginning of the disk to the closest alignment boundary. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

#### Remarks

- If the **size** and **offset** parameters aren't specified, the logical partition is created in the largest disk extent available in the extended partition.

## Examples

To create a logical partition of 1000 megabytes in size, in the extended partition of the selected disk, type:

```
create partition logical size=1000
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [create command](create)
- [select disk](select-disk)