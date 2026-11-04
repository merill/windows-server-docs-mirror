---
layout: Conceptual
title: ntcmdprompt | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ntcmdprompt
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ntcmdprompt command, which runs the command interpreter **Cmd.exe**, rather than **Command.com**, after running a Terminate and Stay Resident (TSR) or after starting the command prompt from within an MS-DOS application.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b1a9b2e4-03a8-1d55-ac59-ae5451bf52fe
document_version_independent_id: 13d735a2-1cb8-09de-2589-351d117fd50e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ntcmdprompt.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ntcmdprompt
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ntcmdprompt.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f6f3a9f2-b97c-ca9d-087e-31c553eb043f
---

# ntcmdprompt | Microsoft Learn

Runs the command interpreter **Cmd.exe**, rather than **Command.com**, after running a Terminate and Stay Resident (TSR) or after starting the command prompt from within an MS-DOS application.

## Syntax

```
ntcmdprompt
```

### Parameters

| Parameter | Description |
| --- | --- |
| /? | Displays help at the command prompt. |

#### Remarks

- When **Command.com** is running, some features of **Cmd.exe**, such as the **doskey** display of command history, aren't available. If you would prefer to run the **Cmd.exe** command interpreter after you've started a Terminate and Stay Resident (TSR) or started the command prompt from within an application based on MS-DOS, you can use the **ntcmdprompt** command. However, keep in mind that the TSR may not be available for use when you are running **Cmd.exe**. You can include the **ntcmdprompt** command in your **Config.nt** file or the equivalent custom startup file in an application's program information file (Pif).

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)