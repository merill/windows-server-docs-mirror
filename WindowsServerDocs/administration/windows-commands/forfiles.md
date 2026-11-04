---
layout: Conceptual
title: forfiles | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/forfiles
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for forfiles command, which selects and runs a command on a file or set of files.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-05-20T00:00:00.0000000Z
locale: en-us
document_id: 4b1a260b-a509-ffcd-1132-4c1fb7694e6e
document_version_independent_id: a14e97c6-be2f-3a3a-7452-3fcc734fa63d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/forfiles.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/forfiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/forfiles.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: 748cd3dc-49d5-e0d9-9ca6-768e3686eb93
---

# forfiles | Microsoft Learn

Selects and runs a command on a file or set of files. This command is most commonly used in batch files.

## Syntax

```
forfiles [/P pathname] [/M searchmask] [/S] [/C command] [/D [+ | -] [{<date> | <days>}]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /P `<pathname>` | Specifies the path from which to start the search. By default, searching starts in the current working directory. |
| /M `<searchmask>` | Searches files according to the specified search mask. The default searchmask is `*`. |
| /S | Instructs the **forfiles** command to search in subdirectories recursively. |
| /C `<command>` | Runs the specified command on each file. Command strings should be wrapped in double quotes. The default command is `"cmd /c echo @file"`. |
| /D `[{+\|-}][{<date> | <days>}]` | Selects files with a last modified date within the specified time frame:<br>- Selects files with a last modified date later than or equal to (**+**) or earlier than or equal to (**-**) the specified date, where *date* is in the same regional format as your Windows device, for example MM/DD/YYYY for English (United States).<br>- Selects files with a last modified date later than or equal to (**+**) the current date plus the number of days specified, or earlier than or equal to (**-**) the current date minus the number of days specified.<br>- Valid values for *days* include any number in the range 0-32,768. If no sign is specified, **+** is used by default. |
| /? | Displays the help text in the cmd window. |

#### Remarks

- The `forfiles /S` command is similar to `dir /S`.
- You can use the following variables in the command string as specified by the **/C** command-line option:

    | Variable | Description |
    | --- | --- |
    | @FILE | File name. |
    | @FNAME | File name without extension. |
    | @EXT | File name extension. |
    | @PATH | Full path of the file. |
    | @RELPATH | Relative path of the file. |
    | @ISDIR | Evaluates to TRUE if a file type is a directory. Otherwise, this variable evaluates to FALSE. |
    | @FSIZE | File size, in bytes. |
    | @FDATE | Last modified date stamp on the file. |
    | @FTIME | Last modified time stamp on the file. |
- The **forfiles** command lets you run a command on or pass arguments to multiple files. For example, you could run the **type** command on all files in a tree with the .txt file name extension. Or you could execute every batch file (\*.bat) on drive C, with the file name Myinput.txt as the first argument.
- This command can:

    - Select files by an absolute date or a relative date by using the **/d** parameter.
    - Build an archive tree of files by using variables such as @FSIZE and @FDATE.
    - Differentiate files from directories by using the @ISDIR variable.
    - Include special characters in the command line by using the hexadecimal code for the character, in 0x*HH* format (for example, 0x09 for a tab).
- This command works by implementing the `recurse subdirectories` flag on tools that are designed to process only a single file.

### Examples

To list all of the batch files on drive C, type:

```
forfiles /P c:\ /S /M *.bat /C "cmd /c echo @file is a batch file"
```

To list all of the directories on drive C, type:

```
forfiles /P c:\ /S /M * /C "cmd /c if @isdir==TRUE echo @file is a directory"
```

To list all of the files in the current directory that are at least one year old, type:

```
forfiles /S /M *.* /D -365 /C "cmd /c echo @file is at least one year old."
```

To display the text *file* is outdated for each of the files in the current directory that are older than January 1, 2007, type:

```
forfiles /S /M *.* /D -01/01/2007 /C "cmd /c echo @file is outdated."
```

To list the file name extensions of all the files in the current directory in column format, and add a tab before the extension, type:

```
forfiles /S /M *.* /C "cmd /c echo The extension of @file is 0x09@ext"
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)