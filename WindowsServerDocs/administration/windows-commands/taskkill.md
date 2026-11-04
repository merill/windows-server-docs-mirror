---
layout: Conceptual
title: taskkill | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/taskkill
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the taskkill command, which ends one or more tasks or processes.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e0b8071a-5b86-ecd5-03c7-812817a8381c
document_version_independent_id: 5e20f32a-766a-f4b0-fe17-075abe7f825d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/taskkill.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/taskkill
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/taskkill.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 3567a43c-7703-72ca-9c7e-d1df58e147c4
---

# taskkill | Microsoft Learn

Ends one or more tasks or processes. Processes can be ended by process ID or image name. You can use the [tasklist command](tasklist) command to determine the process ID (PID) for the process to be ended.

Note

This command replaces the **kill** tool.

## Syntax

```
taskkill [/s <computer> [/u [<domain>\]<username> [/p [<password>]]]] {[/fi <filter>] [...] [/pid <processID> | /im <imagename>]} [/f] [/t]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /s `<computer>` | Specifies the name or IP address of a remote computer (do not use backslashes). The default is the local computer. |
| /u `<domain>\<username>` | Runs the command with the account permissions of the user who is specified by `<username>` or by `<domain>\<username>`. The **/u** parameter can be specified only if **/s** is also specified. The default is the permissions of the user who is currently logged on to the computer that is issuing the command. |
| /p `<password>` | Specifies the password of the user account that is specified in the **/u** parameter. |
| /fi `<filter>` | Applies a filter to select a set of tasks. You can use more than one filter or use the wildcard character (`*`) to specify all tasks or image names. The valid filters are listed in the **Filter names, operators, and values** section of this article. |
| /pid `<processID>` | Specifies the process ID of the process to be terminated. |
| /im `<imagename>` | Specifies the image name of the process to be terminated. Use the wildcard character (`*`) to specify all image names. |
| /f | Specifies that processes be forcefully ended. This parameter is ignored for remote processes; all remote processes are forcefully ended. |
| /t | Ends the specified process and any child processes started by it. |

#### Filter names, operators, and values

| Filter Name | Valid Operators | Valid Value(s) |
| --- | --- | --- |
| STATUS | eq, ne | `RUNNING | NOT RESPONDING | UNKNOWN` |
| IMAGENAME | eq, ne | Image name |
| PID | eq, ne, gt, lt, ge, le | PID value |
| SESSION | eq, ne, gt, lt, ge, le | Session number |
| CPUtime | eq, ne, gt, lt, ge, le | CPU time in the format *HH:MM:SS*, where *MM* and *SS* are between 0 and 59 and *HH* is any unsigned number |
| MEMUSAGE | eq, ne, gt, lt, ge, le | Memory usage in KB |
| USERNAME | eq, ne | Any valid user name (`<user>` or `<domain\user>`) |
| SERVICES | eq, ne | Service name |
| WINDOWTITLE | eq, ne | Window title |
| MODULES | eq, ne | DLL name |

## Remarks

- The **WINDOWTITLE** and **STATUS** filters aren't supported when a remote system is specified.
- The wildcard character (`*`) is accepted for the `*/im` option, only when a filter is applied.
- Ending a remote process is always carried out forcefully, regardless whether the **/f** option is specified.
- Providing a computer name to the hostname filter causes a shutdown, stopping all processes.

## Examples

To end the processes with process IDs *1230*, *1241*, and *1253*, type:

```
taskkill /pid 1230 /pid 1241 /pid 1253
```

To forcefully end the process *Notepad.exe* if it was started by the system, type:

```
taskkill /f /fi "USERNAME eq NT AUTHORITY\SYSTEM" /im notepad.exe
```

To end all processes on the remote computer *Srvmain* with an image name beginning with *note*, while using the credentials for the user account *Hiropln*, type:

```
taskkill /s srvmain /u maindom\hiropln /p p@ssW23 /fi "IMAGENAME eq note*" /im *
```

To end the process with the process ID *2134* and any child processes that it started, but only if those processes were started by the Administrator account, type:

```
taskkill /pid 2134 /t /fi "username eq administrator"
```

To end all processes that have a process ID *greater than or equal to 1000*, regardless of their image names, type:

```
taskkill /f /fi "PID ge 1000" /im *
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [tasklist command](tasklist)