---
layout: Conceptual
title: select vdisk | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/select-vdisk
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the select vdisk command, which selects the specified virtual hard disk (VHD) and shifts the focus to it.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 033415dd-9011-d797-6fd8-35cf783017ab
document_version_independent_id: 831f58ed-9c3e-5c2b-d423-d9f903b24724
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/select-vdisk.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/select-vdisk
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/select-vdisk.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bbcf3ec2-32eb-a6b2-b11a-b7daafd3274d
---

# select vdisk | Microsoft Learn

Selects the specified virtual hard disk (VHD) and shifts the focus to it.

## Syntax

```
select vdisk file=<full path> [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| file=`<full path>` | Specifies the full path and file name of an existing VHD file. |
| noerr | Used for scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To shift the focus to the VHD named *c:\test\test.vhd*, type:

```
select vdisk file=c:\test\test.vhd
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [attach vdisk](attach-vdisk)
- [compact vdisk](compact-vdisk)
- [detach vdisk](detach-vdisk)
- [detail vdisk](detail-vdisk)
- [expand vdisk](expand-vdisk)
- [merge vdisk](merge-vdisk)
- [list](list)
- [select disk command](select-disk)
- [select partition command](select-partition)
- [select volume command](select-volume)