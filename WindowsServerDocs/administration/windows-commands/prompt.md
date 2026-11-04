---
layout: Conceptual
title: prompt | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/prompt
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the prompt command, which customizes your Cmd.exe command prompt.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: 1a9e75b9-f667-9b12-eda1-94e44182135d
document_version_independent_id: 866008d5-06e9-0e2c-1813-3f9514c033d4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/prompt.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/prompt
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/prompt.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 93a47d23-0a88-57aa-2906-b11f1b28b84e
---

# prompt | Microsoft Learn

Changes the Cmd.exe command prompt, including displaying any text you want, such as the name of the current directory, the time and date, or the Microsoft Windows version number. If used without parameters, this command resets the command prompt to the default setting, which is the current drive letter and directory followed by the greater than symbol (**&gt;**).

## Syntax

```
prompt [<text>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<text>` | Specifies the text and information that you want to include in the command prompt. |
| /? | Displays help at the command prompt. |

#### Remarks

- The character combinations you can include instead of, or in addition to, one or more character strings in the *text* parameter:

    | Character | Description |
    | --- | --- |
    | $q | = (Equal sign) |
    | $$ | $ (Dollar sign) |
    | $t | Current time |
    | $d | Current date |
    | $p | Current drive and path |
    | $v | Windows version number |
    | $n | Current drive |
    | $g | &gt; (Greater than sign) |
    | $l | &lt; (Less than sign) |
    | $b | `|` (Pipe symbol) |
    | $\_ | ENTER-LINEFEED |
    | $e | ANSI escape code (code 27) |
    | $h | Backspace (to delete a character that has been written to the command line) |
    | $a | & (Ampersand) |
    | $c | ( (Left parenthesis) |
    | $f | ) (Right parenthesis) |
    | $s | Space |
- When command extensions are enabled the **prompt** command supports the following formatting characters:

    | Character | Description |
    | --- | --- |
    | $+ | Zero or more plus sign (**+**) characters, depending on the depth of the **pushd** directory stack (one character for each level pushed). |
    | $m | The remote name associated with the current drive letter or the empty string if current drive is not a network drive. |
- If you include the **$p** character in the text parameter, your disk is read after you enter each command (to determine the current drive and path). This can take extra time, especially for floppy disk drives.

### Examples

To set a two-line command prompt with the current time and date on the first line and the greater than sign on the next line, type:

```
prompt $d$s$s$t$_$g
```

The prompt is changed as follows, where the date and time are current:

```
Fri 06/01/2007  13:53:28.91
```

To set the command prompt to display as an arrow (`-->`), type:

```
prompt --$g
```

To manually change the command prompt to the default setting (the current drive and path followed by the greater than sign), type:

```
prompt $p$g
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)