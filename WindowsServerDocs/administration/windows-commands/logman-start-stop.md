---
layout: Conceptual
title: logman start and logman stop | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/logman-start-stop
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the logman start and logman stop commands, which starts a data collector and sets the begin time to manual, or stops a Data Collector Set and sets the end time to manual.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 03fe4dfa-455b-d7c7-2aae-cc4d95e2e702
document_version_independent_id: 83e265c0-3157-2c2c-e852-57cd222c0cb3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/logman-start-stop.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/logman-start-stop
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/logman-start-stop.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 624c4153-6ee3-1d29-9851-1bca54f68cf2
---

# logman start and logman stop | Microsoft Learn

The **logman start** command starts a data collector and sets the begin time to manual. The **logman stop** command stops a Data Collector Set and sets the end time to manual.

## Syntax

```
logman start <[-n] <name>> [options]
logman stop <[-n] <name>> [options]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -s `<computer name>` | Perform the command on the specified remote computer. |
| -config `<value>` | Specifies the settings file containing command options. |
| [-n] `<name>` | Specifies the name of the target object. |
| -ets | Sends commands to Event Trace Sessions directly, without saving or scheduling. |
| -as | Performs the requested operation asynchronously. |
| -? | Displays context-sensitive help. |

### Examples

To start the data collector *perf\_log*, on the remote computer *server\_1*, type:

```
logman start perf_log -s server_1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [logman command](logman)