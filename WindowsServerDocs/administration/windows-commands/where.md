---
layout: Conceptual
title: where | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/where
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for where, which displays the location of files that match the given search pattern.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 407ed947-7f5f-80c0-8ad7-61bf2e87396a
document_version_independent_id: b597038c-6869-d634-d076-13200445b554
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/where.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/where
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/where.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: d4aa5f1b-bc82-2674-24fe-93360bee8123
---

# where | Microsoft Learn

Displays the location of files that match the given search pattern.

## Syntax

```
where [/r <Dir>] [/q] [/f] [/t] [$<ENV>:|<Path>:]<Pattern>[ ...]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /r &lt;Dir&gt; | Indicates a recursive search, starting with the specified directory. |
| /q | Returns an exit code (**0** for success, **1** for failure) without displaying the list of matched files. |
| /f | Displays the results of the **where** command in quotation marks. |
| /t | Displays the file size and the last modified date and time of each matched file. |
| [$&lt;ENV&gt;:|&lt;Path&gt;:]&lt;Pattern&gt;[ ...] | Specifies the search pattern for the files to match. At least one pattern is required, and the pattern can include wildcard characters (**\*** and **?**). By default, **where** searches the current directory and the paths that are specified in the PATH environment variable. You can specify a different path to search by using the format $*ENV*:*Pattern* (where *ENV* is an existing environment variable containing one or more paths) or by using the format *Path*:*Pattern* (where *Path* is the directory path you want to search). These optional formats should not be used with the **/r** command-line option. |
| /? | Displays help at the command prompt. |

## Remarks

- If you do not specify a file name extension, the extensions listed in the PATHEXT environment variable are appended to the pattern by default.
- **Where** can run recursive searches, display file information such as date or size, and accept environment variables in place of paths on local computers.

## Examples

To find all files named Test in drive C of the current computer and its subdirectories, type:

```
where /r c:\ test
```

To list all files in the Public directory, type:

```
where $public:*.*
```

To find all files named Notepad in drive C of the remote computer, Computer1, and its subdirectories, type:

```
where /r \\computer1\c notepad.*
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)