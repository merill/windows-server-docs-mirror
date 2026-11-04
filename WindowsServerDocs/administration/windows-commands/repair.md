---
layout: Conceptual
title: repair | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/repair
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the repair command, which repairs RAID-5 volumes by replacing the failed disk region with a specified dynamic disk.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: fa1dc7dc-6670-80b6-84af-9d26074591be
document_version_independent_id: 88b9c702-8005-b00f-145d-df5fcdc402be
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/repair.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/repair
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/repair.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ad523515-48fb-05cd-8f44-22968370c21d
---

# repair | Microsoft Learn

Repairs the RAID-5 volume with focus by replacing the failed disk region with the specified dynamic disk.

A volume in a RAID-5 array must be selected for this operation to succeed. Use the **select volume** command to select a volume and shift the focus to it.

## Syntax

```
repair disk=<n> [align=<n>] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| disk=`<n>` | Specifies the dynamic disk that will replace the failed disk region. Where *n* must have free space greater than or equal to the total size of the failed disk region in the RAID-5 volume. |
| align=`<n>` | Aligns all volume or partition extents to the closest alignment boundary. Where *n* is the number of kilobytes (KB) from the beginning of the disk to the closest alignment boundary. |
| noerr | for scripting only. When an error is encountered, DiskPart continues to process commands as if the error didn't occur. Without this parameter, an error causes DiskPart to exit with an error code. |

### Examples

To replace the volume with focus by replacing it with dynamic disk 4, type:

```
repair disk=4
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select volume command](select-volume)