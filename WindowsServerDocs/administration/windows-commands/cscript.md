---
layout: Conceptual
title: cscript | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/cscript
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the cscript command, which starts a script so that it runs in a command-line environment.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1411dbfd-80a5-af91-704a-0b69f341a84e
document_version_independent_id: 6d6547d9-f200-6736-2b89-f4719f176c73
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/cscript.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/cscript
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/cscript.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: bd3ecc2f-7d4e-61b9-a5ea-1f5f811b0cb6
---

# cscript | Microsoft Learn

Starts a script to run in a command-line environment.

Important

Performing this task does not require you to have administrative credentials. Therefore, as a security best practice, consider performing this task as a user without administrative credentials.

## Syntax

```
cscript <scriptname.extension> [/b] [/d] [/e:<engine>] [{/h:cscript | /h:wscript}] [/i] [/job:<identifier>] [{/logo | /nologo}] [/s] [/t:<seconds>] [x] [/u] [/?] [<scriptarguments>]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| scriptname.extension | Specifies the path and file name of the script file with optional file name extension. |
| /b | Specifies batch mode, which does not display alerts, scripting errors, or input prompts. |
| /d | Starts the debugger. |
| /e:`<engine>` | Specifies the engine that is used to run the script. |
| /h:cscript | Registers cscript.exe as the default script host for running scripts. |
| /h:wscript | Registers wscript.exe as the default script host for running scripts. The default. |
| /i | Specifies interactive mode, which displays alerts, scripting errors, and input prompts. The default, and the opposite of `/b`. |
| /job:`<identifier>` | Runs the job identified by *identifier* in a .wsf script file. |
| /logo | Specifies that the Windows Script Host banner is displayed in the console before the script runs. The default, and the opposite of `/nologo`. |
| /nologo | Specifies that the Windows Script Host banner is not displayed before the script runs. |
| /s | Saves the current command-prompt options for the current user. |
| /t:`<seconds>` | Specifies the maximum time the script can run (in seconds). You can specify up to 32,767 seconds. The default is no time limit. |
| /u | Specifies Unicode for input and output that is redirected from the console. |
| /x | Starts the script in the debugger. |
| /? | Displays available command parameters and provides help for using them. The same as typing **cscript.exe** with no parameters and no script. |
| scriptarguments | Specifies the arguments passed to the script. Each script argument must be preceded by a slash (**/**). |

#### Remarks

- Each parameter is optional; however, you can't specify script arguments without specifying a script. If you don't specify a script or any script arguments, cscript.exe displays the cscript.exe syntax and the valid host options.
- The **/t** parameter prevents excessive running of scripts by setting a timer. When the run time exceeds the specified value, cscript interrupts the script engine and ends the process.
- Windows script files usually have one of the following file name extensions: .wsf, .vbs, .js. Windows Script Host can use .wsf script files. Each .wsf file can use multiple scripting engines and perform multiple jobs.
- if you double-click a script file with an extension that has no association, the **Open With** dialog box appears. Select wscript or cscript, and then select **Always use this program to open this file type**. This registers wscript.exe or cscript as the default script host for files of this file type.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)