---
layout: Conceptual
title: pause | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pause
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pause command, which suspends the processing of batch programs.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 8131ffdf-4999-a198-912c-c3a471392893
document_version_independent_id: 7a7b89db-e683-ecf9-13de-fa08dc6908ac
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pause.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pause
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pause.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: 2330576d-02a0-05ad-9fbb-e1e4f525ceb7
---

# pause | Microsoft Learn

Suspends the processing of a batch program, displaying the prompt, `Press any key to continue . . .`

## Syntax

```
pause
```

### Parameters

| Parameter | Description |
| --- | --- |
| /? | Displays help at the command prompt. |

## Remarks

- If you press CTRL+C to stop a batch program, the following message appears, `Terminate batch job (Y/N)?`. If you press **Y** (for yes) in response to this message, the batch program ends and control returns to the operating system.
- You can insert the **pause** command before a section of the batch file that you might not want to process. When **pause** suspends processing of the batch program, you can press CTRL+C and then press **Y** to stop the batch program.

## Examples

To create a batch program that prompts the user to change disks in one of the drives, type:

```
@echo off
:Begin
copy a:*.*
echo Put a new disk into Drive A
pause
goto begin
```

In this example, all the files on the disk in Drive A are copied to the current directory. After the message prompts you to put a new disk in Drive A, the **pause** command suspends processing so that you can change disks and then press any key to resume processing. This batch program runs in an endless loop—the **goto begin** command sends the command interpreter to the Begin label of the batch file.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)