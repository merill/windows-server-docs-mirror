---
layout: Conceptual
title: unexpose | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/unexpose
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the unexpose command, which unexposes an exposed shadow copy.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 8a8bba4b-7855-fcd9-31cc-d7d250be2dab
document_version_independent_id: 5c10671d-409b-1c0c-4004-92b3bd6bb70d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/unexpose.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/unexpose
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/unexpose.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 020ce9cf-5328-b559-826e-8004994205da
---

# unexpose | Microsoft Learn

Unexposes a shadow copy that was exposed by using the [expose command](expose). The exposed shadow copy can be specified by its Shadow ID, drive letter, share, or mount point.

## Syntax

```
unexpose {<shadowID> | <drive:> | <share> | <mountpoint>}
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<shadowID>` | Displays the shadow copy specified by the given Shadow ID. You can use an existing alias or an environment variable in place of `<shadowID>`. Use the [add command](add) without parameters to see all existing aliases. |
| `<drive:>` | Displays the shadow copy associated with the specified drive letter (for example, drive P). |
| `<share>` | Displays the shadow copy associated with the specified share (for example, `\\MachineName`). |
| `<mountpoint>` | Displays the shadow copy associated with the specified mount point (for example, `C:\shadowcopy\`). |
| add | Used without parameters will show you the existing aliases. |

## Examples

To unexpose the shadow copy associated with \*drive P:\*, type:

```
unexpose P:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [add command](add)
- [expose command](expose)