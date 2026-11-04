---
layout: Conceptual
title: serverweroptin | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/serverweroptin
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the serverweroptin command, which allows you to turn on error reporting.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 18ed2dfe-1e20-a30a-53ea-8bd381c60e6d
document_version_independent_id: 77f8f368-84ec-5e3e-c87b-14b254b3f299
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/serverweroptin.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/serverweroptin
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/serverweroptin.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cd5a07b0-b993-12dd-0e1f-2dedc16d082f
---

# serverweroptin | Microsoft Learn

Allows you to turn on error reporting.

## Syntax

```
serverweroptin [/query] [/detailed] [/summary]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /query | Verifies your current setting. |
| /detailed | Specifies to send detailed reports automatically. |
| /summary | Specifies to send summary reports automatically. |
| /? | Displays help at the command prompt. |

## Examples

To verify the current setting, type:

```
serverweroptin /query
```

To automatically send detailed reports, type:

```
serverweroptin /detailed
```

To automatically send summary reports, type:

```
serverweroptin /summary
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)