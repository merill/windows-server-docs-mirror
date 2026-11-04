---
layout: Conceptual
title: list | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/list
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the list command, which displays a list of disks, of partitions in a disk, of volumes in a disk, or of virtual hard disks (VHDs).
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d3047a26-15fe-acdc-538f-eaa729a0fe48
document_version_independent_id: 50258c2e-b5cd-6391-4432-4b4f7fb2bd91
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/list.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/list
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/list.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e882e30b-901c-d8d2-d056-afcc69f8f032
---

# list | Microsoft Learn

Displays a list of disks, of partitions in a disk, of volumes in a disk, or of virtual hard disks (VHDs).

## Syntax

```
list { disk | partition | volume | vdisk }
```

### Parameters

| Parameter | Description |
| --- | --- |
| disk | Displays a list of disks and information about them, such as their size, amount of available free space, whether the disk is a basic or dynamic disk, and whether the disk uses the master boot record (MBR) or GUID partition table (GPT) partition style. |
| partition | Displays the partitions listed in the partition table of the current disk. |
| volume | Displays a list of basic and dynamic volumes on all disks. |
| vdisk | Displays a list of the VHDs that are attached and/or selected. This command lists detached VHDs if they are currently selected; however, the disk type is set to Unknown until the VHD is attached. The VHD marked with an asterisk (\*) has focus. |

#### Remarks

- When listing partitions on a dynamic disk, the partitions might not correspond to the dynamic volumes on the disk. This discrepancy occurs because dynamic disks contain entries in the partition table for the system volume or boot volume (if present on the disk). They also contain a partition that occupies the remainder of the disk in order to reserve the space for use by dynamic volumes.
- The object marked with an asterisk (\*) has focus.
- When listing disks, if a disk is missing, its disk number is prefixed with M. For example, the first missing disk is numbered *M0*.

### Examples

```
list disk
list partition
list volume
list vdisk
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)