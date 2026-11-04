---
layout: Conceptual
title: remove | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/remove
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the remove command, which removes a drive letter or mount point from a volume.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 87fee592-b7dd-c9a6-1abd-d774cd90197b
document_version_independent_id: 65b4088a-7fa2-b17b-a8a3-abfe9293c16f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/remove.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/remove
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/remove.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae28cdca-f573-3f3a-fe90-e1d8cbe40ed5
---

# remove | Microsoft Learn

Removes a drive letter or mount point from the volume with focus. If the all parameter is used, all current drive letters and mount points are removed. If no drive letter or mount point is specified, then DiskPart removes the first drive letter or mount point it encounters.

The remove command can also be used to change the drive letter associated with a removable drive. You can't remove the drive letters on system, boot, or paging volumes. In addition, you can't remove the drive letter for an OEM partition, any GPT partition with an unrecognized GUID, or any of the special, non-data, GPT partitions such as the EFI system partition.

Note

A volume must be selected for the **remove** command to succeed. Use the [select volume](select-volume) command to select a disk and shift the focus to it.

## Syntax

```
remove [{letter=<drive> | mount=<path> [all]}] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| letter=`<drive>` | The drive letter to remove. |
| mount=`<path>` | The mount point path to remove. |
| all | Removes all current drive letters and mount points. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

### Examples

To remove the d:\ drive, type:

```
remove letter=d
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)