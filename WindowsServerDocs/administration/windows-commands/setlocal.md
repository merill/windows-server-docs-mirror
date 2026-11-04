---
layout: Conceptual
title: setlocal | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/setlocal
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the setlocal command, which starts localization of environment variables in a batch file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 2c1319ea-20fb-948f-dc98-622d106439ca
document_version_independent_id: d8e5fe91-62d8-1565-f625-dbde41df0dec
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/setlocal.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/setlocal
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/setlocal.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: f3afd670-6283-7855-9120-2c403ec7c10c
---

# setlocal | Microsoft Learn

Starts localization of environment variables in a batch file. Localization continues until a matching **endlocal** command is encountered or the end of the batch file is reached.

## Syntax

```
setlocal [enableextensions | disableextensions] [enabledelayedexpansion | disabledelayedexpansion]
```

### Parameters

| Parameter | Description |
| --- | --- |
| enableextensions | Enables the command extensions until the matching **endlocal** command is encountered, regardless of the setting before the **setlocal** command was run. |
| disableextensions | Disables the command extensions until the matching **endlocal** command is encountered, regardless of the setting before the **setlocal** command was run. |
| enabledelayedexpansion | Enables the delayed environment variable expansion until the matching **endlocal** command is encountered, regardless of the setting before the **setlocal** command was run. |
| disabledelayedexpansion | Disables the delayed environment variable expansion until the matching **endlocal** command is encountered, regardless of the setting before the **setlocal** command was run. |
| /? | Displays help at the command prompt. |

#### Remarks

- If you use **setlocal** outside of a script or batch file, it has no effect.
- Use **setlocal** to change environment variables when you run a batch file. Environment changes made after you run **setlocal** are local to the batch file. The Cmd.exe program restores previous settings when it encounters an **endlocal** command or reaches the end of the batch file.
- You can have more than one **setlocal** or **endlocal** command in a batch program (that is, nested commands).
- The **setlocal** command sets the ERRORLEVEL variable. If you pass {**enableextensions** | **disableextensions**} or {**enabledelayedexpansion** | **disabledelayedexpansion**}, the ERRORLEVEL variable is set to **0** (zero). Otherwise, it's set to **1**. You can use this information in batch scripts to determine whether the extensions are available, as shown in the following example:

    ```
    verify other 2>nul
    setlocal enableextensions
    if errorlevel 1 echo Unable to enable extensions
    ```

    Because **cmd** does not set the ERRORLEVEL variable when command extensions are disabled, the **verify** command initializes the ERRORLEVEL variable to a nonzero value when you use it with an invalid argument. Also, if you use the **setlocal** command with arguments {**enableextensions** | **disableextensions**} or {**enabledelayedexpansion** | **disabledelayedexpansion**} and it does not set the ERRORLEVEL variable to **1**, command extensions are not available.

## Examples

To localize environment variables in a batch file, follow this sample script:

```
rem *******Begin Comment**************
rem This program starts the superapp batch program on the network,
rem directs the output to a file, and displays the file
rem in Notepad.
rem *******End Comment**************
@echo off
setlocal
path=g:\programs\superapp;%path%
call superapp>c:\superapp.out
endlocal
start notepad c:\superapp.out
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)