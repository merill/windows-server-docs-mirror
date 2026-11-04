---
layout: Conceptual
title: rem | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/rem
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the rem command, which records comments in a script, batch, or config.sys file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 0f57efb2-68c8-ceee-9243-83b670c9c437
document_version_independent_id: a3056411-fc71-f377-09d5-f6f452149b8b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/rem.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/rem
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/rem.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1c7dd4ea-c01d-97d6-7815-ae7c575e9b7d
---

# rem | Microsoft Learn

Records comments in a script, batch, or config.sys file. If no comment is specified, **rem** adds vertical spacing.

Note

This command is internal to the command-line interpreter, cmd.exe.

## Syntax

```
rem [<comment>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<comment>` | Specifies a string of characters to include as a comment. |
| /? | Displays help at the command prompt. |

#### Remarks

- The **rem** command doesn't display comments on the screen. To display comments on the screen, you must include the **echo on** command in your file.
- You can't use a redirection character (`<` or `>`) or pipe (`|`) in a batch file comment.
- Although you can use **rem** without a comment to add vertical spacing to a batch file, you can also use blank lines. Blank lines are ignored when a batch program is processed.

### Examples

To add vertical spacing through batch file comments, type:

```
@echo off
rem  This batch program formats and checks new disks.
rem  It is named Checknew.bat.
rem
rem echo Insert new disk in Drive B.
pause
format b: /v chkdsk b:
```

To include an explanatory comment before the **prompt** command in a config.sys file, type:

```
rem Set prompt to indicate current directory
prompt $p$g
```

To provide a comment about what a script does, type:

```
rem The commands in this script set up 3 drives.
rem The first drive is a primary partition and is
rem assigned the letter D. The second and third drives
rem are logical partitions, and are assigned letters
rem E and F.
create partition primary size=2048
assign d:
create partition extended
create partition logical size=2048
assign e:
create partition logical
assign f:
```

For multi-line comments, use conditional execution:

```
  Rem/||(
    The REM statement evaluates to success,
    so these lines will never be executed.
    Keep in mind that you will need to escape closing parentheses
    within multi-line comment blocks like shown in this example. ^)
  )
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)