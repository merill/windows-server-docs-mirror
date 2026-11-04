---
layout: Conceptual
title: add | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/add_2
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the add command, which adds a disk or volume in an existing RAID configuration.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-10-12T00:00:00.0000000Z
locale: en-us
document_id: cb642cdc-6208-8018-8fc5-930a101a76f9
document_version_independent_id: cb642cdc-6208-8018-8fc5-930a101a76f9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/add_2.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/add_2
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/add_2.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3dfa5f80-e10a-f9e0-a8dd-2cb399fac367
---

# add | Microsoft Learn

Mirrors the simple volume with focus to the specified active disk.

Note

This DiskPart command isn't available in any edition of Windows Vista.

## Syntax

```
add disk=<n> [align=<n>] [wait] [noerr]
```

## Parameters

| Parameter | Description |
| --- | --- |
| disk=`<n>` | Specifies a disk, other than the one containing the existing simple volume, to contain the mirror. You can mirror only simple volumes. The specified disk must have unallocated space at least as large as the size of the simple volume you want to mirror. |
| align=`<n>` | Typically used with hardware RAID Logical Unit Number (LUN) arrays to improve performance. Aligns all volume or partition extents to the closest alignment boundary. `n` is the number of kilobytes (KB) from the beginning of the disk to the closest alignment boundary. |
| wait | Waits for the volume to finish synchronizing with the added disk before returning. Without this parameter, DiskPart returns after the mirrored volume is created and doesn't wait for the synchronization to complete. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error didn't occur. Without this parameter, an error causes DiskPart to exit with an error code. |

### Remarks

- A volume must be selected for this operation to succeed. Use the select volume command to select a volume and shift the focus to it.

## Examples

To create a mirror of the volume with focus on disk 2, type:

```
add disk=2
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)