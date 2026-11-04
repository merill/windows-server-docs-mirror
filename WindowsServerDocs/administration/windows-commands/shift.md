---
layout: Conceptual
title: shift | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/shift
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the shift command, which changes the position of batch parameters in a batch file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 25664c13-3d7f-7c92-a7d0-0fd68d89f0b4
document_version_independent_id: 4a1b99aa-5ef6-b881-7483-16ae4bbdd577
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/shift.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/shift
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/shift.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: ff97cf5e-5925-a115-1196-91627be1ea32
---

# shift | Microsoft Learn

Changes the position of batch parameters in a batch file.

## Syntax

```
shift [/n <N>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /n `<N>` | Specifies to start shifting at the *N*th argument, where *N* is any value from *0* to *8*. Requires command extensions, which are enabled by default. |
| /? | Displays help at the command prompt. |

## Remarks

- The **shift** command changes the values of the batch parameters **%0** through **%9** by copying each parameter into the previous one—the value of **%1** is copied to **%0**, the value of **%2** is copied to **%1**, and so on. This is useful for writing a batch file that performs the same operation on any number of parameters.
- If command extensions are enabled, the **shift** command supports the **/n** command-line option. The **/n** option specifies to start shifting at the Nth argument, where **N** is any value from 0 to 8. For example, **SHIFT /2** would shift **%3** to **%2**, **%4** to **%3**, and so on, and leave **%0** and **%1** unaffected. Command extensions are enabled by default.
- You can use the **shift** command to create a batch file that can accept more than 10 batch parameters. If you specify more than 10 parameters on the command line, those that appear after the tenth (**%9**) will be shifted one at a time into **%9**.
- The **shift** command has no effect on the **%\*** batch parameter.
- There's no backward **shift** command. After you implement the **shift** command, you can't recover the batch parameter (**%0**) that existed before the shift.

## Examples

To use a batch file, called *Mycopy.bat*, to copy a list of files to a specific directory, type:

```
@echo off
rem MYCOPY.BAT copies any number of files
rem to a directory.
rem The command uses the following syntax:
rem mycopy dir file1 file2 ...
set todir=%1
:getfile
shift
if "%1"=="" goto end
copy %1 %todir%
goto getfile
:end
set todir=
echo All done
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)