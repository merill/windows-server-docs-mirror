---
layout: Conceptual
title: logman update | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/logman-update
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the logman update command, which updates an existing data collector.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9639b4e0-2238-1798-2c7d-c08d6bab3e4b
document_version_independent_id: 9b74fcec-3aed-62eb-e4c4-8cac28366892
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/logman-update.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/logman-update
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/logman-update.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 43e72f0f-9db4-e49d-f855-2874072a39b6
---

# logman update | Microsoft Learn

Updates an existing data collector.

## Syntax

```
logman update <counter | trace | alert | cfg | api> <[-n] <name>> [options]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [logman update counter](logman-update-counter) | Updates a counter data collector. |
| [logman update alert](logman-update-alert) | Updates an alert data collector. |
| [logman update cfg](logman-update-cfg) | Updates a configuration data collector. |
| [logman update api](logman-update-api) | Updates an API tracing data collector. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [logman command](logman)