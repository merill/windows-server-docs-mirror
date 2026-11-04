---
layout: Conceptual
title: more | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/more
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the more command, which displays one screen of output at a time.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2019-07-26T00:00:00.0000000Z
locale: en-us
document_id: 5d966c34-6d6c-f54e-8b71-9f3583d43f73
document_version_independent_id: 8484f296-dbd7-6b19-ecf8-0cb9848a6049
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/more.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/more
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/more.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: de5cbeb5-4c60-2878-bd73-1f0ceb0fdd13
---

# more | Microsoft Learn

Displays one screen of output at a time.

Note

The **more** command, with different parameters, is also available from the Recovery Console.

## Syntax

```
<command> | more [/c] [/p] [/s] [/t<n>] [+<n>]
more [[/c] [/p] [/s] [/t<n>] [+<n>]] < [<drive>:][<path>]<filename>
more [/c] [/p] [/s] [/t<n>] [+<n>] [<files>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<command>` | Specifies a command for which you want to display the output. |
| /c | Clears the screen before displaying a page. |
| /p | Expands form-feed characters. |
| /s | Displays multiple blank lines as a single blank line. |
| /t`<n>` | Displays tabs as the number of spaces specified by *n*. |
| +`<n>` | Displays the first file, beginning at the line specified by *n*. |
| `[<drive>:][<path>]<filename>` | Specifies the location and name of a file to display. |
| `<files>` | Specifies a list of files to display. Files must be separated using spaces. |
| /? | Displays help at the command prompt. |

#### Remarks

- The following subcommands are accepted at the **more** prompt (`-- More --`), including:

    | Key | Action |
    | --- | --- |
    | SPACEBAR | Press the **SPACEBAR** to display the next screen. |
    | ENTER | Press **ENTER** to display the file one line at a time. |
    | f | Press **F** to display the next file listed on the command line. |
    | q | Press **Q** to quit the **more** command. |
    | = | Shows the line number. |
    | p `<n>` | Press **P** to display the next *n* lines. |
    | s `<n>` | Press **S** to skip the next *n* lines. |
    | ? | Press **?** to show the commands that are available at the **more** prompt. |
- If you use the redirection character (`<`), you must also specify a file name as the source.
- If you use the pipe (`|`), you can use such commands as **dir**, **sort**, and **type**.

### Examples

To view the first screen of information of a file named *Clients.new*, type one of the following commands:

```
more < clients.new
type clients.new | more
```

The **more** command displays the first screen of information from Clients.new, and you can press the SPACEBAR to see the next screen of information.

To clear the screen and remove all extra blank lines before displaying the file *Clients.new*, type one of the following commands:

```
more /c /s < clients.new
type clients.new | more /c /s
```

To display the current line number at the **more** prompt, type:

```
more =
```

The current line number is added to the **more** prompt, as `-- More [Line: 24] --`

To display a specific number of lines at the **more** prompt, type:

```
more p
```

The **more** prompt asks you for the number of lines to display, as follows: `-- More -- Lines:`. Type the number of lines to display, and then press ENTER. The screen changes to show only that number of lines.

To skip a specific number of lines at the **more** prompt, type:

```
more s
```

The **more** prompt asks you for the number of lines to skip, as follows: `-- More -- Lines:`. Type the number of lines to skip, and then press ENTER. The screen changes to show that those lines are skipped.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Windows Recovery Environment (WinRE)](/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)