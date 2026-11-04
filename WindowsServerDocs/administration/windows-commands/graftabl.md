---
layout: Conceptual
title: graftabl | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/graftabl
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the graftabl command, which enables Windows operating systems to display an extended character set in graphics mode.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1bcda751-29e6-5541-0bcd-7b3f7a5e9d94
document_version_independent_id: 24314f2c-5492-10da-deac-fc97f88dc671
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/graftabl.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/graftabl
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/graftabl.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6620929f-96f3-488c-fccd-cf8ffed6ccd4
---

# graftabl | Microsoft Learn

Enables Windows operating systems to display an extended character set in graphics mode. If used without parameters, **graftabl** displays the previous and the current code page.

Important

The **graftabl** command is a legacy command, and therefore outdated. It is normally not installed in modern Windows versions. Please see the [chcp](chcp) page for codepage handling.

## Syntax

```
graftabl <codepage>
graftabl /status
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<codepage>` | Specifies a code page to define the appearance of extended characters in graphics mode. Valid code page identification numbers are:<br>- **437** - United States<br>- **850** - Multilingual (Latin I)<br>- **852** - Slavic (Latin II)<br>- **855** - Cyrillic (Russian)<br>- **857** - Turkish<br>- **860** - Portuguese<br>- **861** - Icelandic<br>- **863** - Canadian-French<br>- **865** - Nordic<br>- **866** - Russian<br>- **869** - Modern Greek |
| /status | Displays the current code page being used by this command. |
| /? | Displays help at the command prompt. |

#### Remarks

- The **graftabl** command affects only the monitor display of extended characters of the code page that you specify. It doesn't change the actual console input code page. To change the console input code page, use the [mode](mode) or [chcp](chcp) command.
- Each exit code and a brief description of it:

    | Exit code | Description |
    | --- | --- |
    | 0 | Character set was loaded successfully. No previous code page was loaded. |
    | 1 | An incorrect parameter was specified. No action was taken. |
    | 2 | A file error occurred. |
- You can use the ERRORLEVEL environment variable in a batch program to process exit codes that are returned by **graftabl**.

### Examples

To view the current code page used by **graftabl**, type:

```
graftabl /status
```

To load the graphics character set for code page 437 (United States) into memory, type:

```
graftabl 437
```

To load the graphics character set for code page 850 (multilingual) into memory, type:

```
graftabl 850
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [freedisk command](freedisk)
- [mode command](mode)
- [chcp command](chcp)