---
layout: Conceptual
title: list shadows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/list-shadows
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the list shadows command, which lists persistent and existing non-persistent shadow copies that are on the system.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 59b10ada-9fb7-ef8a-13cf-528f11d47625
document_version_independent_id: 45f1cf0b-f6b1-ff68-8341-7a06a18adbe7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/list-shadows.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/list-shadows
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/list-shadows.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 56360d6e-6863-d530-d9f0-55f497bc2d5f
---

# list shadows | Microsoft Learn

Lists persistent and existing non-persistent shadow copies that are on the system.

## Syntax

```
list shadows {all | set <setID> | id <shadowID>}
```

### Parameters

| Parameter | Description |
| --- | --- |
| all | Lists all shadow copies. |
| set `<setID>` | Lists shadow copies that belong to the specified Shadow Copy Set ID. |
| id `<shadowID>` | Lists any shadow copy with the specified shadow copy ID. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)