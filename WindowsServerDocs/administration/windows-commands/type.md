---
layout: Conceptual
title: type | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/type
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the type command, which displays the contents of a text file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-10-16T00:00:00.0000000Z
locale: en-us
document_id: a57abddd-edac-51ba-f486-eec44ccce2e7
document_version_independent_id: d3b1f63a-646e-6f57-a3fc-9c1b99875c89
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/type.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/type
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/type.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: c38c8253-f0cc-bf74-e1b2-4d4347a6f651
---

# type | Microsoft Learn

In the Windows Command shell, **type** is a built in command which displays the contents of a text file. Use the **type** command to view a text file without modifying it.

In PowerShell, **type** is a built-in alias to the [Get-Content cmdlet](/en-us/powershell/module/microsoft.powershell.management/get-content), which also displays the contents of a file, but using a different syntax.

## Syntax

```
type [<drive>:][<path>]<filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<drive>:][<path>]<filename>` | Specifies the location and name of the file or files that you want to view. If your `<filename>` contains spaces, you must enclose it in quotation marks (for example, "Filename Containing Spaces.txt"). You can also add multiple filenames by adding spaces between them. |
| /? | Displays help at the command prompt. |

#### Remarks

- If you display a binary file or a file that is created by a program, you may see strange characters on the screen, including formfeed characters and escape-sequence symbols. These characters represent control codes that are used in the binary file. In general, avoid using the **type** command to display binary files.

## Examples

To display the contents of a file named *holiday.mar*, type:

```
type holiday.mar
```

To display the contents of a lengthy file named *holiday.mar* one screen at a time, type:

```
type holiday.mar | more
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)