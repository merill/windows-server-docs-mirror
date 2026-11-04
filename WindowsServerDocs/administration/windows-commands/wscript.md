---
layout: Conceptual
title: wscript | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wscript
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wscript command; wscript provides an environment in which users can execute scripts in various languages that use various object models to perform tasks.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-04-01T00:00:00.0000000Z
locale: en-us
document_id: b6d64a4e-816e-d545-6c37-c2b1f24174ef
document_version_independent_id: c828776b-914b-31e7-158c-3bf672b496f8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wscript.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wscript
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wscript.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: d2353621-3690-31b1-7e2a-146f5a94c3dd
---

# wscript | Microsoft Learn

Applies to: Windows Server (All supported versions)

Windows Script Host provides an environment in which users can execute scripts in various languages that use various object models to perform tasks.

## Syntax

```
wscript [<scriptname>] [/b] [/d] [/e:<engine>] [{/h:cscript|/h:wscript}] [/i] [/job:<identifier>] [{/logo|/nologo}] [/s] [/t:<number>] [/x] [/?] [<ScriptArguments>]
```

## Parameters

| Parameter | Description |
| --- | --- |
| `scriptname` | Specifies the path and file name of the script file. |
| `/b` | Specifies batch mode, which doesn't display alerts, scripting errors, or input prompts. The /b parameter is the opposite of **/i**. |
| `/d` | Starts the debugger. |
| `/e` | Specifies the engine that is used to run the script. This parameter lets you run scripts that use a custom file name extension. Without the /e parameter, you can only run scripts that use registered file name extensions. For example, if you try to run this command:`cscript test.admin`You receive this error message: Input Error: There's no script engine for file extension `.admin`.One advantage of using nonstandard file name extensions is that it guards against accidentally double-selecting a script and running something you didn't actually want to run. Using this extension doesn't create a permanent association between the `.admin` file name extension and VBScript. Each time you run a script that uses a `.admin` file name extension, you need to use the /e parameter. |
| `/h:cscript` | Registers **cscript.exe** as the default script host for running scripts. |
| `/h:wscript` | Registers **wscript.exe** as the default script host for running scripts. This behavior is the default when the **/h** option is omitted. |
| `/i` | Specifies interactive mode, which displays alerts, scripting errors, and input prompts.The /i parameter is the default and the opposite of **/b**. |
| `/job:\<identifier>` | Runs the job identified by *identifier* in a **.wsf** script file. |
| `/logo` | Specifies that the Windows Script Host banner is displayed in the console before the script runs.The /logo parameter is the default and the opposite of **/nologo**. |
| `/nologo` | Specifies that the Windows Script Host banner isn't displayed before the script runs. The /nologo parameter is the opposite of **/logo**. |
| `/s` | Saves the current command prompt options for the current user. |
| `/t:\<number>` | Specifies the maximum time the script can run (in seconds). You can specify up to 32,767 seconds. The default is no time limit. |
| `/x` | Starts the script in the debugger. |
| `ScriptArguments` | Specifies the arguments passed to the script. Each script argument must be preceded with a slash (/). |
| `/?` | Displays Help at the command prompt. |

## Remarks

- Performing this task doesn't require you to have administrative credentials. Consider performing this task as a user without administrative credentials as a security best practice.
- To open a command prompt, on the **Start** screen, type **cmd**, and then select **command prompt**.
- Each parameter is optional. However you can't specify script arguments without specifying a script. If you don't specify a script or any script arguments, **wscript.exe** displays the **Windows Script Host Settings** dialog box. Use the dialog box to set global scripting properties for all scripts that **wscript.exe** runs on the local computer.
- The **/t** parameter prevents excessive running of scripts by setting a timer. When the time exceeds the specified value, **wscript** interrupts the script engine and ends the process.
- Windows script files usually have one of the following file name extensions: **.wsf**, **.vbs**, **.js**.
- If you double-select a script file with an extension that has no association, the **Open With** dialog box appears. Select **wscript** or **cscript**, and then select **Always use this program to open this file type**. This registers **wscript.exe** or **cscript.exe** as the default script host for files of this file type.
- You can set properties for individual scripts. For more information about Windows Script Host, see [Windows Script Host overview](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc738350%28v=ws.10%29).
- Windows Script Host can use **.wsf** script files. Each **.wsf** file can use multiple scripting engines and perform multiple jobs.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)