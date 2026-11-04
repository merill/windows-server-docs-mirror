---
layout: Conceptual
title: title | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/title
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the title command, which creates a title for the Command Prompt window.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f05b63c9-f06b-4b8c-5348-3b0117ac0035
document_version_independent_id: 7c99c37f-2a03-0051-4c54-7bdafacb714b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/title.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/title
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/title.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7edce41f-9d20-1f40-84ae-8ba9e490284b
---

# title | Microsoft Learn

Creates a title for the Command Prompt window.

## Syntax

```
title [<string>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<string>` | Specifies the text to appear as the title of the Command Prompt window. |
| /? | Displays help at the command prompt. |

#### Remarks

- To create window title for batch programs, include the **title** command at the beginning of a batch program.
- After a window title is set, you can reset it only by using the **title** command.

## Examples

To change the Command Prompt window title to *Updating Files* while the batch file executes the **copy** command, and then to return the title back to *Command Prompt*, type the following script:

```
@echo off
title Updating Files
copy \\server\share\*.xls c:\users\common\*.xls
echo Files Updated.
title Command Prompt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)