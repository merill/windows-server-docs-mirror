---
layout: Conceptual
title: attributes disk | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/attributes-disk
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the attributes disk command, which displays, sets, or clears the attributes of a disk.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c6fd1d3c-6647-d573-c1a0-3b0409da103d
document_version_independent_id: bd56eeaa-9c4e-a57c-bb0a-939d720d7940
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/attributes-disk.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/attributes-disk
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/attributes-disk.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: e80cd96f-30e6-2f36-c627-bf0d46cfb165
---

# attributes disk | Microsoft Learn

Displays, sets, or clears the attributes of a disk. When this command is used to display the current attributes of a disk, the startup disk attribute denotes the disk used to start the computer. For a dynamic mirror, it displays the disk that contains the boot plex of the boot volume.

Important

A disk must be selected for the **attributes disk** command to succeed. Use the **select disk** command to select a disk and shift the focus to it.

## Syntax

```
attributes disk [{set | clear}] [readonly] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| set | Sets the specified attribute of the disk with focus. |
| clear | Clears the specified attribute of the disk with focus. |
| readonly | Specifies that the disk is read-only. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To view the attributes of the selected disk, type:

```
attributes disk
```

To set the selected disk as read-only, type:

```
attributes disk set readonly
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select disk command](select-disk)