---
layout: Conceptual
title: goto | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/goto
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the goto command, which directs cmd.exe to a labeled line in a batch program.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: dd43ce44-5d30-7425-336b-58a7fc731c3f
document_version_independent_id: 68adad7a-0a26-2fad-d7c1-d9df45311ebd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/goto.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/goto
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/goto.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: ed9e14b4-c0e2-8dd4-9d1b-c0ae191e96ac
---

# goto | Microsoft Learn

Directs cmd.exe to a labeled line in a batch program. Within a batch program, this command directs command processing to a line that is identified by a label. When the label is found, processing continues starting with the commands that begin on the next line.

## Syntax

```
goto <label>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<label>` | Specifies a text string that is used as a label in the batch program. |
| /? | Displays help at the command prompt. |

#### Remarks

- If command extensions are enabled (the default), and you use the **goto** command with a target label of **:EOF**, you transfer control to the end of the current batch script file and exit the batch script file without defining a label. When you use this command with the **:EOF** label, you must insert a colon before the label. For example: `goto:EOF`.
- You can use spaces in the *label* parameter, but you can't include other separators (for example, semicolons (;) or equal signs (=)).
- The *label* value that you specify must match a label in the batch program. The label within the batch program must begin with a colon (:). If a line begins with a colon, it's treated as a label and any commands on that line are ignored. If your batch program doesn't contain the label that you specify in the *label* parameter, then the batch program stops and displays the following message: `Label not found`.
- You can use **goto** with other commands to perform conditional operations. For more information about using **goto** for conditional operations, see the [if command](if).

## Examples

The following batch program formats a disk in drive A as a system disk. If the operation is successful, the **goto** command directs processing to the **:end** label:

```
echo off
format a: /s
if not errorlevel 1 goto end
echo An error occurred during formatting.
:end
echo End of batch program.
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [cmd command](cmd)
- [if command](if)