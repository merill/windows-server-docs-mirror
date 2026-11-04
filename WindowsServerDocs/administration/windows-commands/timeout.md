---
layout: Conceptual
title: timeout | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/timeout
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the timeout command, which pauses the command processor for the specified number of seconds.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: cac8c242-eb47-2c37-050c-96d5880ae38f
document_version_independent_id: aa146643-e0d1-98fb-011c-fa1fc695d83d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/timeout.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/timeout
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/timeout.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: 877a9ea4-a06d-cb01-1899-3b77f1e85b05
---

# timeout | Microsoft Learn

Pauses the command processor for the specified number of seconds. This command is typically used in batch files.

## Syntax

```
timeout /t <timeoutinseconds> [/nobreak]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /t `<timeoutinseconds>` | Specifies the decimal number of seconds (between -1 and 99999) to wait before the command processor continues processing. The value **-1** causes the computer to wait indefinitely for a keystroke. |
| /nobreak | Specifies to ignore user key strokes. |
| /? | Displays help at the command prompt. |

#### Remarks

- A user keystroke resumes the command processor execution immediately, even if the timeout period has not expired.
- When used in conjunction with the resource kit's **Sleep** tool, **timeout** is similar to the **pause** command.

## Examples

To pause the command processor for ten seconds, type:

```
timeout /t 10
```

To pause the command processor for 100 seconds and ignore any keystroke, type:

```
timeout /t 100 /nobreak
```

To pause the command processor indefinitely until a key is pressed, type:

```
timeout /t -1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)