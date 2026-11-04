---
layout: Conceptual
title: convert dynamic | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/convert-dynamic
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the convert dynamic command, which converts a basic disk into a dynamic disk.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 843821e4-cbab-da62-392b-d2dba6a4d3b4
document_version_independent_id: 4abffe46-63bc-73eb-ebb1-c89129121ecb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/convert-dynamic.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/convert-dynamic
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/convert-dynamic.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 69800a7f-f4ac-feed-eacb-40a98baa9466
---

# convert dynamic | Microsoft Learn

Converts a basic disk into a dynamic disk. A basic disk must be selected for this operation to succeed. Use the [select disk command](select-disk) to select a basic disk and shift the focus to it.

Note

For instructions regarding how to use this command, see [Change a Dynamic Disk Back to a Basic Disk](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc755238%28v=ws.11%29)).

## Syntax

```
convert dynamic [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

#### Remarks

- Any existing partitions on the basic disk become simple volumes.

## Examples

To convert a basic disk into a dynamic disk, type:

```
convert dynamic
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [convert command](convert)