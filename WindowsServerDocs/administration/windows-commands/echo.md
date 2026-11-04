---
layout: Conceptual
title: echo | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/echo
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the echo command, which displays messages or turns on or off the command echoing feature.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-10-02T00:00:00.0000000Z
locale: en-us
document_id: b73a4605-c4b3-46a8-ec4e-493751fff82b
document_version_independent_id: 2bcfea05-35c7-49cb-0570-a0d5a4957ca1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/echo.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/echo
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/echo.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e57d4cb9-1144-75a9-8934-dd94498978a5
---

# echo | Microsoft Learn

Displays messages or turns on or off the command echoing feature. If used without parameters, **echo** displays the current echo setting.

## Syntax

```
echo [<message>]
echo [on | off]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [on | off] | Turns on or off the command echoing feature. Command echoing is on by default. |
| `<message>` | Specifies the text to display on the screen. |
| /? | Displays help at the command prompt. |

#### Remarks

- The `echo <message>` command is more useful when **echo** is turned off. To display a message that is several lines long without displaying any commands, you can include several `echo <message>` commands after the **echo off** command in your batch program.
- After **echo** is turned off, the command prompt doesn't appear in the Command Prompt window. To display the command prompt, type **echo on.**
- If used in a batch file, **echo on** and **echo off** don't affect the setting at the command prompt.
- If there's an empty variable in a batch file while using **echo**, it displays "ECHO is off". To prevent seeing this message, and produce a blank line instead, place a colon (`:`) between **echo** and the variable. For example, `echo:%var%`.
- To prevent echoing a particular command in a batch file, insert an (`@`) sign in front of the command. To prevent echoing all commands in a batch file, include the **echo off** command at the beginning of the file.
- To display an exclamation mark (`!`) in batch scripts, wrap the word or phrase in double quotes followed by a caret before the exclamation mark (`"Hello World^!"`). Alternatively, a double caret (`^^`) can be used without the need for double quotes (`Hello World^^!`).
- To display a pipe (`|`), ampersand (`&`) or redirection character (`<` or `>`) when you're using **echo**, use a caret (`^`) immediately before that character. For example, `^|`, `^&`, `^>`, or `^<`. To display a caret, type two carets in succession (`^^`).
- When inside a block terminated by parentheses (`()`), both opening and closing parentheses must also be escaped using the caret (`^`) immediately before each one. For example, `This is ^(now^) correct` will correctly display `This is (now) correct`.

### Examples

To display the current **echo** setting, type:

```
echo
```

To echo a blank line on the screen, type:

```
echo.
```

Note

Don't include a space before the period. Otherwise, the period appears instead of a blank line.

To prevent echoing commands at the command prompt, type:

```
echo off
```

Note

When **echo** is turned off, the command prompt doesn't appear in the Command Prompt window. To display the command prompt again, type **echo on**.

To prevent all commands in a batch file (including the **echo off** command) from displaying on the screen, on the first line of the batch file type:

```
@echo off
```

You can use the **echo** command as part of an **if** statement. For example, to search the current directory for any file with the .rpt file name extension, and to echo a message if such a file is found, type:

```
if exist *.rpt echo The report has arrived.
```

The following batch file searches the current directory for files with the .txt file name extension, and displays a message indicating the results of the search:

```
@echo off
if not exist *.txt (
echo This directory contains no text files.
) else (
   echo This directory contains the following text file^(s^):
   echo.
   dir /b *.txt
   )
```

If no .txt files are found when the batch file is run, the following message displays:

```
This directory contains no text files.
```

If .txt files are found when the batch file is run the following output displays (for this example, assume the files File1.txt, File2.txt, and File3.txt exist):

```
This directory contains the following text file(s):

File1.txt
File2.txt
File3.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)