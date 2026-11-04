---
layout: Conceptual
title: delete shadows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/delete-shadows
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the delete shadows command, which deletes shadow copies.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 41a5809a-03fd-c7d3-dca6-fe399e49f3e0
document_version_independent_id: 3898abf3-9428-1f2e-a59d-5c91d837a582
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/delete-shadows.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/delete-shadows
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/delete-shadows.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ecd215ff-e719-efee-0928-79bad214d227
---

# delete shadows | Microsoft Learn

Deletes shadow copies.

## Syntax

```
delete shadows [all | volume <volume> | oldest <volume> | set <setID> | id <shadowID> | exposed {<drive> | <mountpoint>}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| all | Deletes all shadow copies. |
| volume `<volume>` | Deletes all shadow copies of the given volume. |
| oldest `<volume>` | Deletes the oldest shadow copy of the given volume. |
| set `<setID>` | Deletes the shadow copies in the Shadow Copy Set of the given ID. You can specify an alias by using the **%** symbol if the alias exists in the current environment. |
| id `<shadowID>` | Deletes a shadow copy of the given ID. You can specify an alias by using the **%** symbol if the alias exists in the current environment. |
| exposed {`<drive>` | `<mountpoint>`} | Deletes shadow copies exposed at the specified drive or mount point. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [delete command](delete)