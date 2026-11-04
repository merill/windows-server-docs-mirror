---
layout: Conceptual
title: tasklist | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tasklist
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tasklist command, which displays a list of the processes running on the local or remote computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 154a2487-a931-44ec-7935-ae21e0e23255
document_version_independent_id: 12ecaa21-2665-7a34-2f50-341ffa5eb725
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tasklist.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tasklist
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tasklist.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 9e6a9ba5-a43b-b840-4cf3-d43aba85bd09
---

# tasklist | Microsoft Learn

Displays a list of currently running processes on the local computer or on a remote computer. **Tasklist** replaces the **tlist** tool.

Note

This command replaces the **tlist** tool.

## Syntax

```
tasklist [/s <computer> [/u [<domain>\]<username> [/p <password>]]] [{/m <module> | /svc | /v}] [/fo {table | list | csv}] [/nh] [/fi <filter> [/fi <filter> [ ... ]]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /s `<computer>` | Specifies the name or IP address of a remote computer (do not use backslashes). The default is the local computer. |
| /u `<domain>\<username>` | Runs the command with the account permissions of the user who is specified by `<username>` or by `<domain>\<username>`. The **/u** parameter can be specified only if **/s** is also specified. The default is the permissions of the user who is currently logged on to the computer that is issuing the command. |
| /p `<password>` | Specifies the password of the user account that is specified in the **/u** parameter. |
| /m `<module>` | Lists all tasks with DLL modules loaded that match the given pattern name. If the module name is not specified, this option displays all modules loaded by each task. |
| svc | Lists all the service information for each process without truncation. Valid when the **/fo** parameter is set to **table**. |
| /v | Displays verbose task information in the output. For complete verbose output without truncation, use **/v** and **/svc** together. |
| /fo `{table | list | csv}` | Specifies the format to use for the output. Valid values are **table**, **list**, and **csv**. The default format for output is **table**. |
| /nh | Suppresses column headers in the output. Valid when the **/fo** parameter is set to **table** or **csv**. |
| /fi `<filter>` | Specifies the types of processes to include in or exclude from the query. You can use more than one filter or use the wildcard character (`\`) to specify all tasks or image names. The valid filters are listed in the **Filter names, operators, and values** section of this article. |
| /? | Displays help at the command prompt. |

#### Filter names, operators, and values

| Filter Name | Valid Operators | Valid Value(s) |
| --- | --- | --- |
| STATUS | eq, ne | `RUNNING | NOT RESPONDING | UNKNOWN`. This filter isn't supported if you specify a remote system. |
| IMAGENAME | eq, ne | Image name |
| PID | eq, ne, gt, lt, ge, le | PID value |
| SESSION | eq, ne, gt, lt, ge, le | Session number |
| SESSIONNAME | eq, ne | Session name |
| CPUtime | eq, ne, gt, lt, ge, le | CPU time in the format *HH:MM:SS*, where *MM* and *SS* are between 0 and 59 and *HH* is any unsigned number |
| MEMUSAGE | eq, ne, gt, lt, ge, le | Memory usage in KB |
| USERNAME | eq, ne | Any valid user name (`<user>` or `<domain\user>`) |
| SERVICES | eq, ne | Service name |
| WINDOWTITLE | eq, ne | Window title. This filter isn't supported if you specify a remote system. |
| MODULES | eq, ne | DLL name |

## Examples

To list all tasks with a *process ID greater than 1000*, and *display them in csv format*, type:

```
tasklist /v /fi "PID gt 1000" /fo csv
```

To list the system processes that are currently running, type:

```
tasklist /fi "USERNAME ne NT AUTHORITY\SYSTEM" /fi "STATUS eq running"
```

To list detailed information for all processes that are currently running, type:

```
tasklist /v /fi "STATUS eq running"
```

To list all the service information for processes on the remote computer *srvmain*, which has a DLL name *beginning with ntdll*, type:

```
tasklist /s srvmain /svc /fi "MODULES eq ntdll*"
```

To list the processes on the remote computer *srvmain*, using the credentials of your currently logged-on user account, type:

```
tasklist /s srvmain
```

To list the processes on the remote computer *srvmain*, using the credentials of the *user account Hiropln*, type:

```
tasklist /s srvmain /u maindom\hiropln /p p@ssW23
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)