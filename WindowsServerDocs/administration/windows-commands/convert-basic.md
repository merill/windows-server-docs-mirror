---
layout: Conceptual
title: convert basic | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/convert-basic
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the convert basic command, which converts an empty dynamic disk to a basic disk.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c141f68d-7da4-262e-1c61-0b213de71f3a
document_version_independent_id: 26cb74a2-ce9e-d786-f039-fab488f1f0f6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/convert-basic.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/convert-basic
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/convert-basic.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 58ea2e1e-3b17-3805-0c83-56bfd5471bcd
---

# convert basic | Microsoft Learn

Converts an empty dynamic disk to a basic disk. A dynamic disk must be selected for this operation to succeed. Use the [select disk command](select-disk) to select a dynamic disk and shift the focus to it.

Important

The disk must be empty to convert it to a basic disk. Back up your data, and then delete all partitions or volumes before converting the disk.

Note

For instructions regarding how to use this command, see [Change a Dynamic Disk Back to a Basic Disk](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc755238%28v=ws.11%29)).

## Syntax

```
convert basic [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To convert the selected dynamic disk to basic, type:

```
convert basic
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [convert command](convert)