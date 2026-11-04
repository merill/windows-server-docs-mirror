---
layout: Conceptual
title: path | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/path
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for setting the command path in the PATH environment variable, specifying the set of directories used to search for executable (.exe) files.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7b20eed0-caa5-60b4-5212-bfd0cde965cc
document_version_independent_id: a8cddc32-9e0a-9102-3a55-86b16fe6fdd6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/path.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/path
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/path.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 14f32508-297b-406a-38b9-3fdc90abd370
---

# path | Microsoft Learn

Sets the command path in the PATH environment variable, specifying the set of directories used to search for executable (.exe) files. If used without parameters, this command displays the current command path.

## Syntax

```
path [[<drive>:]<path>[;...][;%PATH%]]
path ;
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<drive>:]<path>` | Specifies the drive and directory to set in the command path. The current directory is always searched before the directories specified in the command path. |
| ; | Separates directories in the command path. If used without other parameters, **;** clears the existing command paths from the PATH environment variable and directs Cmd.exe to search only in the current directory. |
| `%PATH%` | Appends the command path to the existing set of directories listed in the PATH environment variable. If you include this parameter, Cmd.exe replaces it with the command path values found in the PATH environment variable, eliminating the need to manually enter these values at the command prompt. |
| /? | Displays help at the command prompt. |

## Remarks

- The Windows operating system searches using default file name extensions in the following order of precedence: .exe, .com, .bat, and .cmd. Which means if you're looking for a batch file named, acct.bat, but have an app named acct.exe in the same directory, you must include the .bat extension at the command prompt.
- If two or more files in the command path have the same file name and extension, this command first searches for the specified file name in the current directory. Then, it searches the directories in the command path in the order that they're listed in the PATH environment variable.
- If you place the **path** command in your Autoexec.nt file, the Windows operating system automatically appends the specified MS-DOS subsystem search path every time you log on to your computer. Cmd.exe does not use the Autoexec.nt file. When started from a shortcut, Cmd.exe inherits the environment variables set in My Computer/Properties/Advanced/Environment.

## Examples

To search the paths *c:\user\taxes*, *b:\user\invest*, and *b:\bin* for external commands, type:

```
path c:\user\taxes;b:\user\invest;b:\bin
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)