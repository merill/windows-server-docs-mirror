---
layout: Conceptual
title: refsutil iometrics | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/refsutil-iometrics
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the refsutil iometrics tool, which tracks IO data to monitor performance and usage patterns on a Resilient File System (ReFS) volume in Windows.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-02T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 5afc3164-ba09-fbd6-1514-daaa9f919033
document_version_independent_id: 5afc3164-ba09-fbd6-1514-daaa9f919033
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/refsutil-iometrics.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/refsutil-iometrics
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/refsutil-iometrics.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 8479d8c0-c31c-ae8c-cf14-91de71c5e387
---

# refsutil iometrics | Microsoft Learn

The `refsutil iometrics` command allows you to query or set volume heat parameters for tracking input/output (IO) metrics on a ReFS (Resilient File System) volume. This tool helps monitor and manage the performance and usage patterns on the volume.

## Syntax

```
refsutil iometrics <drive> <[/q]> | <[/s] [/st <seconds>] [/sp <seconds>] [/sg <number>]>
```

## Parameters

| Parameters | Description |
| --- | --- |
| `<drive>` | Specifies the drive letter of the volume to be compressed in the format `E:`. |
| `/q` | Queries the current volume activity tracking settings. |
| `/s` | Configures the volume activity tracking settings. |
| `/st <seconds>` | Specifies how long in seconds the volume should track IO activity. |
| `/sp <seconds>` | Specifies how often in seconds the IO metrics should be tracked. |
| `/sg <number>` | Specifies the number of periods to track per volume tracking unit. |

ReFS enforces values for `/st`, `/sp`, and `/sg` to be within suitable ranges and adjusts them to the filesystem minimums if needed. These values can be omitted, in which case ReFS uses default settings. The current minimum values are:

- `/st`: 3,600 seconds (1 hour)
- `/sp`: 10 seconds
- `/sg`: 5 periods

## Examples

To query the volume activity tracking settings on the F: drive, run the command:

```
refsutil iometrics F: /q
```

To set the volume activity tracking settings on drive F: with default values, run the command:

```
refsutil iometrics F: /s
```

To set the volume activity tracking settings on drive F: to track IO activity for 604,800 seconds or 7 (seven) days, run the command:

```
refsutil iometrics F: /s /st 604800
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)