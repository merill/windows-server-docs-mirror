---
layout: Conceptual
title: exit | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/exit
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for exit, which exits the diskpart command interpreter.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-10-12T00:00:00.0000000Z
locale: en-us
document_id: efe5000f-9b39-feaa-f21c-8ae40a3e790d
document_version_independent_id: 8257a294-47c9-0242-ae78-389410599c26
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/exit.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/exit
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/exit.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0178e3b6-8cec-c157-4f43-fbb1f4763551
---

# exit | Microsoft Learn

Exits the command interpreter or the current batch script.

## Syntax

```
exit [/b] [<exitcode>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /b | Exits the current batch script instead of exiting Cmd.exe. If executed from outside a batch script, exits Cmd.exe. |
| `<exitcode>` | Specifies a numeric number. If **/b** is specified, the ERRORLEVEL environment variable is set to that number. If you are quitting the command interpreter, the process exit code is set to that number. |
| /? | Displays help at the command prompt. |

## Examples

To close the command interpreter, type:

```
exit
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)