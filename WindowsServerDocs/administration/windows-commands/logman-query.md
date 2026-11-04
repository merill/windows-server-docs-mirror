---
layout: Conceptual
title: logman query | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/logman-query
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the logman query command, which queries data collector or data collector set properties.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 60e44390-5035-c708-d57e-df81e66bdd5e
document_version_independent_id: aab30c48-8ae9-a831-1368-83566c8542d7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/logman-query.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/logman-query
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/logman-query.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3142d0ef-c8ee-2060-3555-79cbcd1181a1
---

# logman query | Microsoft Learn

Queries data collector or data collector set properties.

## Syntax

```
logman query [providers|Data Collector Set name] [options]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -s `<computer name>` | Perform the command on the specified remote computer. |
| -config `<value>` | Specifies the settings file containing command options. |
| [-n] `<name>` | Name of the target object. |
| -ets | Sends commands to Event Trace Sessions directly without saving or scheduling. |
| /? | Displays context-sensitive help. |

### Examples

To list all Data Collector Sets configured on the target system, type:

```
logman query
```

To list the data collectors contained in the Data Collector Set named *perf\_log*, type:

```
logman query perf_log
```

To list all available providers of data collectors on the target system, type:

```
logman query providers
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [logman command](logman)