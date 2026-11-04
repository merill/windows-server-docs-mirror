---
layout: Conceptual
title: create | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/create
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the create command, which creates a partition or shadow partition on a disk, a volume on one or more disks, or a virtual hard disk (VHD).
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: fd814874-ec93-051a-92d7-5a3c2b061f27
document_version_independent_id: bd2dc8ca-543d-5d8b-c78d-1cd5e20c652f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/create.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/create
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/create.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b416b199-b882-7baa-9224-13b3e08ac3e0
---

# create | Microsoft Learn

Creates a partition or shadow on a disk, a volume on one or more disks, or a virtual hard disk (VHD). If you're using this command to create a volume on the shadow disk, you must already have at least one volume in the shadow copy set.

## Syntax

```
create partition
create volume
```

### Parameters

| Parameter | Description |
| --- | --- |
| [create partition primary command](create-partition-primary) | Creates a primary partition on the basic disk with focus. |
| [create partition efi command](create-partition-efi) | Creates an Extensible Firmware Interface (EFI) system partition on a GUID Partition Table (gpt) disk on Itanium-based computers. |
| [create partition extended command](create-partition-extended) | Creates an extended partition on the disk with focus. |
| [create partition logical command](create-partition-logical) | Creates a logical partition in an existing extended partition. |
| [create partition msr command](create-partition-msr) | Creates a Microsoft Reserved (MSR) partition on a GUID partition table (gpt) disk. |
| [create volume simple command](create-volume-simple) | Creates a simple volume on the specified dynamic disk. |
| [create volume mirror command](create-volume-mirror) | Creates a volume mirror by using the two specified dynamic disks. |
| [create volume raid command](create-volume-raid) | Creates a RAID-5 volume using three or more specified dynamic disks. |
| [create volume stripe command](create-volume-stripe) | Creates a striped volume using two or more specified dynamic disks. |

## Examples

You run these commands in the DiskPart interpreter. To start it, type `diskpart` at an elevated command prompt. Each example creates a 1000-megabyte (MB) object; omit the `size` parameter to use the remaining available space. For the full parameter list and behavior of each command, see the linked child article.

Before you create a partition, run `list disk` to identify the intended basic disk, then use the [select disk](select-disk) command to give it focus. In the following example, replace `<disk-number>` with the number of the basic disk you want. To create a 1000-MB primary partition on the disk with focus:

```
select disk <disk-number>
create partition primary size=1000
```

Volume commands create volumes on dynamic disks that you specify by number. To create a 1000-MB simple volume on dynamic disk 1:

```
create volume simple size=1000 disk=1
```

To create a 1000-MB mirrored volume across dynamic disks 1 and 2:

```
create volume mirror size=1000 disk=1,2
```

To create a 1000-MB striped volume across dynamic disks 1 and 2:

```
create volume stripe size=1000 disk=1,2
```

To create a 1000-MB RAID-5 volume across dynamic disks 1, 2, and 3:

```
create volume raid size=1000 disk=1,2,3
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)