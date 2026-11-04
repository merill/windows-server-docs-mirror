---
layout: Conceptual
title: delete partition | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/delete-partition
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the delete partition command, which deletes the partition with focus.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 2bd2a84a-5bee-80af-aa2b-9e67f5d5e058
document_version_independent_id: 62214aea-c3f8-bb11-8951-14c87d1166f4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/delete-partition.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/delete-partition
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/delete-partition.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c00a6153-37e5-5528-0806-0069ebfd5d84
---

# delete partition | Microsoft Learn

Deletes the partition with focus. Before you begin, you must select a partition for this operation to succeed. Use the [select partition](select-partition) command to select a partition and shift the focus to it.

Warning

Deleting a partition on a dynamic disk can delete all dynamic volumes on the disk, destroying any data and leaving the disk in a corrupt state.

You can't delete the system partition, boot partition, or any partition that contains the active paging file or crash dump information.

## Syntax

```
delete partition [noerr] [override]
```

### Parameters

| Parameter | Description |
| --- | --- |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |
| override | Enables DiskPart to delete any partition regardless of type. Typically, DiskPart only permits you to delete known data partitions. |

#### Remarks

- To delete a dynamic volume, always use the [delete volume](delete-volume) command instead.
- Partitions can be deleted from dynamic disks, but they shouldn't be created. For example, it's possible to delete an unrecognized GUID Partition Table (GPT) partition on a dynamic GPT disk. Deleting such a partition doesn't cause the resulting free space to become available. Instead, This command is intended to allow you to reclaim space on a corrupted offline dynamic disk in an emergency situation where the [clean](clean) command in DiskPart can't be used.

## Examples

To delete the partition with focus, type:

```
delete partition
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select partition](select-partition)
- [delete command](delete)
- [delete volume command](delete-volume)
- [clean command](clean)