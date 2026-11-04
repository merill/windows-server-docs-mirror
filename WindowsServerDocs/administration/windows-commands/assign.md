---
layout: Conceptual
title: assign | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/assign
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the assign command, which assigns a drive letter or mount point to the volume with focus.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ce07a41a-ae09-dbc5-9eeb-9e25538113ad
document_version_independent_id: 22bd174c-d174-961b-1210-c1d6510824c6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/assign.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/assign
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/assign.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3eae981e-870e-e1cb-4000-19cbf206ef75
---

# assign | Microsoft Learn

Assigns a drive letter or mount point to the volume with focus. You can also use this command to change the drive letter associated with a removable drive. If no drive letter or mount point is specified, the next available drive letter is assigned. If the drive letter or mount point is already in use, an error is generated.

A volume must be selected for this operation to succeed. Use the **select volume** command to select a volume and shift the focus to it.

Important

You can't assign drive letters to system volumes, boot volumes, or volumes that contain the paging file. In addition, you cannot assign a drive letter to an Original Equipment Manufacturer (OEM) partition or any GUID Partition Table (gpt) partition other than a basic data partition.

## Syntax

```
assign [{letter=<d> | mount=<path>}] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `letter=<d>` | The drive letter you want to assign to the volume. |
| `mount=<path>` | The mount point path you want to assign to the volume. For instructions about how to use this command, see [Assign a mount point folder path to a drive](../../storage/disk-management/assign-a-mount-point-folder-path-to-a-drive). |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To assign the letter E to the volume in focus, type:

```
assign letter=e
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select volume command](select-volume)