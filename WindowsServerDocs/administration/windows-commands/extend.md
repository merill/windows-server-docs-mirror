---
layout: Conceptual
title: extend | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/extend
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the extend command, which extends the volume or partition with focus and its file system into free (unallocated) space on a disk.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e5eb1331-5bcd-9599-33e4-9cda1b081b08
document_version_independent_id: 709a6217-4dad-2a55-e6ed-9d7a83354e0b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/extend.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/extend
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/extend.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3a579a1b-6fba-b83b-e3b7-787ed41ca8a4
---

# extend | Microsoft Learn

Extends the volume or partition with focus and its file system into free (unallocated) space on a disk.

## Syntax

```
extend [size=<n>] [disk=<n>] [noerr]
extend filesystem [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| size=`<n>` | Specifies the amount of space in megabytes (MB) to add to the current volume or partition. If no size is given, all of the contiguous free space that is available on the disk is used. |
| disk=`<n>` | Specifies the disk on which the volume or partition is extended. If no disk is specified, the volume or partition is extended on the current disk. |
| filesystem | Extends the file system of the volume with focus. For use only on disks where the file system was not extended with the volume. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

#### Remarks

- On basic disks, the free space must be on the same disk as the volume or partition with focus. It must also immediately follow the volume or partition with focus (that is, it must start at the next sector offset).
- On dynamic disks with simple or spanned volumes, a volume can be extended to any free space on any dynamic disk. Using this command, you can convert a simple dynamic volume into a spanned dynamic volume. Mirrored, RAID-5 and striped volumes cannot be extended.
- If the partition was previously formatted with the NTFS file system, the file system is automatically extended to fill the larger partition and no data loss will occur.
- If the partition was previously formatted with a file system other than NTFS, the command fails with no change to the partition.
- If the partition was not previously formatted with a file system, the partition will still be extended.
- The partition must have an associated volume before it can be extended.

## Examples

To extend the volume or partition with focus by 500 megabytes, on disk 3, type:

```
extend size=500 disk=3
```

To extend the file system of a volume after it was extended, type:

```
extend filesystem
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)