---
layout: Conceptual
title: logman import and logman export | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/logman-import-export
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for logman import and logman export, which imports a Data Collector Set from an XML file, or exports a Data Collector Set to an XML file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 229d8be7-01db-17d8-c9f7-7300c84604d2
document_version_independent_id: 39f3aa84-ad5f-a4f5-f7a7-e69d0db38a4b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/logman-import-export.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/logman-import-export
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/logman-import-export.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5d465085-e8fb-5903-5e4f-8705e40162d0
---

# logman import and logman export | Microsoft Learn

Imports a Data Collector Set from an XML file, or exports a Data Collector Set to an XML file.

## Syntax

```
logman import <[-n] <name> <-xml <name> [options]
logman export <[-n] <name> <-xml <name> [options]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -s `<computer name>` | Perform the command on the specified remote computer. |
| -config `<value>` | Specifies the settings file containing command options. |
| [-n] `<name>` | Name of the target object. |
| -xml `<name>` | Name of the XML file to import or export. |
| -ets | Sends commands to Event Trace Sessions directly without saving or scheduling. |
| -[-]u `<user [password]>` | Specifies the user to Run As. Entering an `*` for the password produces a prompt for the password. The password is not displayed when you type it at the password prompt. |
| -y | Answers yes to all questions without prompting. |
| /? | Displays context-sensitive help. |

### Examples

To import the XML file *c:\windows\perf\_log.xml* from the computer *server\_1* as a data collector set called *perf\_log*, type:

```
logman import perf_log -s server_1 -xml c:\windows\perf_log.xml
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [logman command](logman)