---
layout: Conceptual
title: logman | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/logman
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the logman command, which creates and manages Event Trace Session and Performance logs and supports many functions of Performance Monitor from the command line.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1061cbd4-258c-f121-cb02-b1c150758dc9
document_version_independent_id: 655ca5a5-0e14-aafc-ea9e-dec3746ffc99
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/logman.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/logman
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/logman.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7abf211a-c216-47a4-8238-2b67c3a59011
---

# logman | Microsoft Learn

Creates and manages Event Trace Session and Performance logs and supports many functions of Performance Monitor from the command line.

## Syntax

```
logman [create | query | start | stop | delete| update | import | export | /?] [options]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [logman create](logman-create) | Creates a counter, trace, configuration data collector, or API. |
| [logman query](logman-query) | Queries data collector properties. |
| [logman start | stop](logman-start-stop) | Starts or stops data collection. |
| [logman delete](logman-delete) | Deletes an existing data collector. |
| [logman update](logman-update) | Updates the properties of an existing data collector. |
| [logman import | export](logman-import-export) | Imports a data collector set from an XML file or export a data collector set to an XML file. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)