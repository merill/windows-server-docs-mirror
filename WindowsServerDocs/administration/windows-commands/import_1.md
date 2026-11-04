---
layout: Conceptual
title: import diskpart | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/import_1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the import command, which imports a foreign disk group into the disk group of the local computer.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ee2a9232-50b6-b3b9-c114-d81c0067f33c
document_version_independent_id: 8e1d0008-074d-6d13-9ef7-f943949930a6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/import_1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/import_1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/import_1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: a51c2300-5c64-c37b-f084-8c8d86328ef8
---

# import diskpart | Microsoft Learn

Imports a foreign disk group into the disk group of the local computer. This command imports every disk that is in the same group as the disk with focus.

> 
> [IMPORTANT] Before you can use this command, you must use the [select disk command](select-disk) to select a dynamic disk in a foreign disk group and shift the focus to it.

## Syntax

```
import [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

### Examples

To import every disk that is in the same disk group as the disk with focus into the disk group of the local computer, type:

```
import
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [diskpart command](diskpart)