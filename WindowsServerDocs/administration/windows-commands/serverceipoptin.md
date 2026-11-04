---
layout: Conceptual
title: serverceipoptin | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/serverceipoptin
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the serverceipoptin, which allows you to participate in the Customer Experience Improvement Program (CEIP).
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 11ab5308-7632-c9ec-bb35-e3fa8f080093
document_version_independent_id: 3ee8fbda-788e-57d9-a563-8b83541aa0bd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/serverceipoptin.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/serverceipoptin
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/serverceipoptin.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3a75f4a5-03a5-fd3c-6237-5bc4600ee457
---

# serverceipoptin | Microsoft Learn

Allows you to participate in the Customer Experience Improvement Program (CEIP).

## Syntax

```
serverceipoptin [/query] [/enable] [/disable]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /query | Verifies your current setting. |
| /enable | Turns on your participation in CEIP. |
| /disable | Turns off your participation in CEIP. |
| /? | Displays help at the command prompt. |

## Examples

To verify your current settings, type:

```
serverceipoptin /query
```

To turn on your participation, type:

```
serverceipoptin /enable
```

To turn off your participation, type:

```
serverceipoptin /disable
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)