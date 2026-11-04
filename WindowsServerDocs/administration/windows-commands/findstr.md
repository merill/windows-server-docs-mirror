---
layout: Conceptual
title: findstr | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/findstr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the findstr command, which searches for patterns of text in files.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 0b90f482-f48a-7d60-7ba9-bb5a1e837989
document_version_independent_id: 5a8e1ac5-3f4d-4da9-67c3-15a08d9a1b61
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/findstr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/findstr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/findstr.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 798c9b11-dc11-8fd1-59dd-65d80462ea7a
---

# findstr | Microsoft Learn

Searches for patterns of text in files.

## Syntax

```
findstr [/b] [/e] [/l | /r] [/s] [/i] [/x] [/v] [/n] [/m] [/o] [/p] [/f:<file>] [/c:<string>] [/g:<file>] [/d:<dirlist>] [/a:<colorattribute>] [/off[line]] <strings> [<drive>:][<path>]<filename>[ ...]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /b | Matches the text pattern if it is at the beginning of a line. |
| /e | Matches the text pattern if it is at the end of a line. |
| /l | Processes search strings literally. |
| /r | Processes search strings as regular expressions. This is the default setting. |
| /s | Searches the current directory and all subdirectories. |
| /i | Ignores the case of the characters when searching for the string. |
| /x | Prints lines that match exactly. |
| /v | Prints only lines that don't contain a match. |
| /n | Prints the line number of each line that matches. |
| /m | Prints only the file name if a file contains a match. |
| /o | Prints character offset before each matching line. |
| /p | Skips files with non-printable characters. |
| /off[line] | Does not skip files that have the offline attribute set. |
| /f:`<file>` | Gets a file list from the specified file. |
| /c:`<string>` | Uses the specified text as a literal search string. |
| /g:`<file>` | Gets search strings from the specified file. |
| /d:`<dirlist>` | Searches the specified list of directories. Each directory must be separated with a semicolon (;), for example `dir1;dir2;dir3`. |
| /a:`<colorattribute>` | Specifies color attributes with two hexadecimal digits. Type `color /?` for additional information. |
| `<strings>` | Specifies the text to search for in *filename*. Required. |
| `[\<drive>:][<path>]<filename>[...]` | Specifies the location and file or files to search. At least one file name is required. |
| /? | Displays Help at the command prompt. |

#### Remarks

- All **findstr** command-line options must precede *strings* and *filename* in the command string.
- Regular expressions use both literal characters and meta-characters to find patterns of text, rather than exact strings of characters.

    - A literal character is a character that doesn't have a special meaning in the regular-expression syntax; instead, it matches an occurrence of that character. For example, letters and numbers are literal characters.
    - A meta-character is a symbol with special meaning (an operator or delimiter) in the regular-expression syntax.

        The accepted meta-characters are:

        | Meta-character | Value |
        | --- | --- |
        | `.` | **Wildcard** - Any character |
        | `*` | **Repeat** - Zero or more occurrences of the previous character or class. |
        | `^` | **Beginning line position** - Beginning of the line. |
        | `$` | **Ending line position** - End of the line. |
        | `[class]` | **Character class** - Any one character in a set. |
        | `[^class]` | **Inverse class** - Any one character not in a set. |
        | `[x-y]` | **Range** - Any characters within the specified range. |
        | `\x` | **Escape** - Literal use of a meta-character. |
        | `\<string` | **Beginning word position** - Beginning of the word. |
        | `string\>` | **Ending word position** - End of the word. |

        The special characters in regular expression syntax have the most power when you use them together. For example, use the combination of the wildcard character (`.`) and repeat (`*`) character to match any string of characters: `.*`

        Use the following expression as part of a larger expression to match any string beginning with *b* and ending with *ing*: `b.*ing`
- To search for multiple strings in a set of files, you must create a text file that contains each search criterion on a separate line.
- Use spaces to separate multiple search strings unless the argument is prefixed with **/c**.

### Examples

To search for *hello* or *there* in file *x.y*, type:

```
findstr hello there x.y
```

To search for *hello there* in file *x.y*, type:

```
findstr /c:"hello there" x.y
```

To find all occurrences of the word *Windows* (with an initial capital letter W) in the file *proposal.txt*, type:

```
findstr Windows proposal.txt
```

To search every file in the current directory and all subdirectories that contained the word *Windows*, regardless of the letter case, type:

```
findstr /s /i Windows *.*
```

To find all occurrences of lines that begin with *FOR* and are preceded by zero or more spaces (as in a computer program loop), and to display the line number where each occurrence is found, type:

```
findstr /b /n /r /c:^ *FOR *.bas
```

To list the exact files that you want to search in a text file, use the search criteria in the file *stringlist.txt*, to search the files listed in *filelist.txt*, and then to store the results in the file *results.out*, type:

```
findstr /g:stringlist.txt /f:filelist.txt > results.out
```

To list every file containing the word *computer* within the current directory and all subdirectories, regardless of case, type:

```
findstr /s /i /m \<computer\> *.*
```

To list every file containing the word computer and any other words that begin with comp, (such as compliment and compete), type:

```
findstr /s /i /m \<comp.* *.*
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)