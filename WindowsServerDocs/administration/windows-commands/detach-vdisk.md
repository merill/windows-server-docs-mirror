---
layout: Conceptual
title: detach vdisk | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/detach-vdisk
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the detach vdisk command, which stops the selected virtual hard disk (VHD) from appearing as a local hard disk drive on the host computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 34149742-26fb-78b3-b92c-6ce64d10fbb5
document_version_independent_id: 7947b120-3fc8-dee8-2984-f2f142bc1d17
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/detach-vdisk.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/detach-vdisk
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/detach-vdisk.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cb0997dc-8978-a838-2f68-078750117859
---

# detach vdisk | Microsoft Learn

Stops the selected virtual hard disk (VHD) from appearing as a local hard disk drive on the host computer. When a VHD is detached, you can copy it to other locations. Before you begin, you must select a VHD for this operation to succeed. Use the [select vdisk](select-vdisk) command to select a VHD and shift the focus to it.

## Syntax

```
detach vdisk [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To detach the selected VHD, type:

```
detach vdisk
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [attach vdisk command](attach-vdisk)
- [compact vdisk command](compact-vdisk)
- [detail vdisk command](detail-vdisk)
- [expand vdisk command](expand-vdisk)
- [Merge vdisk command](merge-vdisk)
- [select vdisk command](select-vdisk)
- [list command](list)