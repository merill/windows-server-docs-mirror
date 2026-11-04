---
layout: Conceptual
title: create partition msr | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/create-partition-msr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for create partition msr, which creates a Microsoft Reserved (MSR) partition on a GUID partition table (gpt) disk.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 643cd509-ba1f-5883-5152-bcc5d06df198
document_version_independent_id: b97a0667-6f1d-c7c8-e20f-f6bc6c5a47e7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/create-partition-msr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/create-partition-msr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/create-partition-msr.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 515edfe7-3925-c99b-22df-2b765a65375c
---

# create partition msr | Microsoft Learn

Creates a Microsoft Reserved (MSR) partition on a GUID partition table (gpt) disk. A Microsoft Reserved partition is required on every gpt disk. The size of this partition depends on the total size of the gpt disk. The size of the gpt disk must be at least 32 MB to create a Microsoft Reserved partition.

Important

Be very careful when using this command. Because gpt disks require a specific partition layout, creating Microsoft Reserved partitions can cause the disk to become unreadable.

A basic gpt disk must be selected for this operation to succeed. You must use the [select disk](select-disk) command to select a basic gpt disk and shift the focus to it.

## Syntax

```
create partition msr [size=<n>] [offset=<n>] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| size=`<n>` | The size of the partition in megabytes (MB). The partition is at least as long in bytes as the number specified by `<n>`. If no size is given, the partition continues until there is no more free space in the current region. |
| offset=`<n>` | Specifies the offset in kilobytes (KB), at which the partition is created. The offset rounds up to completely fill whatever sector size is used. If no offset is given, the partition is placed in the first disk extent that is large enough to hold it. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

#### Remarks

- On gpt disks that are used to boot the Windows operating system, the Extensible Firmware Interface (EFI) system partition is the first partition on the disk, followed by the Microsoft Reserved partition. gpt disks that are used only for data storage do not have an EFI system partition, in which case the Microsoft Reserved partition is the first partition.
- Windows doesn't mount Microsoft Reserved partitions. You cannot store data on them and you cannot delete them.

## Examples

To create a Microsoft Reserved partition of 1000 megabytes in size, type:

```
create partition msr size=1000
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [create command](create)
- [select disk](select-disk)