---
layout: Conceptual
title: bdehdcfg size | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bdehdcfg-size
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bdehdcfg size command, which specifies the size of the system partition when a new system drive is being created.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 695ddeab-46fb-68ea-5747-4550ba352250
document_version_independent_id: 23ce6dda-928d-d63d-488d-4df8118fc3df
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bdehdcfg-size.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bdehdcfg-size
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bdehdcfg-size.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cf6cc8bb-8eed-0963-ded6-48f8f912bd47
---

# bdehdcfg size | Microsoft Learn

Specifies the size of the system partition when a new system drive is being created. If you do not specify a size, the tool will use the default value of 300 MB. The minimum size of the system drive is 100 MB. If you will store system recovery or other system tools on the system partition, you should increase the size accordingly.

Note

The **size** command cannot be combined with the `target <drive_letter> merge` command.

## Syntax

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink} -size <size_in_mb>
```

#### Parameters

| Parameter | Description |
| --- | --- |
| `<size_in_mb>` | Indicates the number of megabytes (MB) to use for the new partition. |

## Examples

To allocate 500 MB to the default system drive:

```
bdehdcfg -target default -size 500
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bdehdcfg](bdehdcfg)