---
layout: Conceptual
title: color | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/color
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the color command, which changes the foreground and background colors in the Command Prompt window for the current session.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-09-19T00:00:00.0000000Z
locale: en-us
document_id: 959d4b23-8fd3-0404-f2b3-9397fbe9dce2
document_version_independent_id: e860e4fa-0075-7df0-0780-cb4f2c86ced3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/color.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/color
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/color.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3b4e73f3-9f25-a16c-e495-2a3ee8594e40
---

# color | Microsoft Learn

Changes the foreground and background colors in the Command Prompt window for the current session. If used without parameters, **color** restores the default Command Prompt window foreground and background colors.

## Syntax

```cmd
color [attr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `attr` | Specifies color attribute of console output. |
| /? | Displays help at the command prompt. |

The following table lists valid hexadecimal digits that you can use as the values for `attr`:

| Value | Color |
| --- | --- |
| 0 | Black |
| 1 | Blue |
| 2 | Green |
| 3 | Aqua |
| 4 | Red |
| 5 | Purple |
| 6 | Yellow |
| 7 | White |
| 8 | Gray |
| 9 | Light blue |
| a | Light green |
| b | Light aqua |
| c | Light red |
| d | Light purple |
| e | Light yellow |
| f | Bright white |

#### Remarks

- You can specify one or two hexadecimal digits. The first is used as the foreground color and the second is used as the background color. If you specify two hexadecimal digits, don't use space characters between them.
- If you specify only one hexadecimal digit, the corresponding color is used as the foreground color and the background color is set to the default color.
- To set the default Command Prompt window color, select the upper-left corner of the **Command Prompt** window, select **Defaults**, select the **Colors** tab, and then select the colors that you want to use for the **Screen Text** and **Screen Background**.
- If you specify the same value for two hexadecimal digits, the ERRORLEVEL is set to `1` and no change is made to either the foreground or the background color.

## Examples

To change the Command Prompt window background color to gray and the foreground color to red, type:

```cmd
color 84
```

To change the Command Prompt window foreground color to light yellow, type:

```cmd
color e
```

Note

In this example, the background is set to the default color because only one hexadecimal digit is specified.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)