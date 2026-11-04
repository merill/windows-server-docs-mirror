---
layout: Conceptual
title: schtasks end | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/schtasks-end
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the schtasks end command, which stops only the instances of a program started by a scheduled task.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-09-16T00:00:00.0000000Z
locale: en-us
document_id: fb79a186-11a1-15f9-def9-0e7969b09f9c
document_version_independent_id: c1d00998-17a2-27f5-ac47-669751d886a5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/schtasks-end.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/schtasks-end
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/schtasks-end.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a35cee5c-c46f-c39c-cd03-a4e30a01eb2a
---

# schtasks end | Microsoft Learn

Stops only the instances of a program started by a scheduled task. To stop other processes, you must use the [TaskKill](taskkill) command.

## Syntax

```
schtasks /end /tn <taskname> [/s <computer> [/u [<domain>\]<user> [/p <password>]]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /tn `<taskname>` | Identifies the task that started the program. This parameter is required. |
| /s `<computer>` | Specifies the name or IP address of a remote computer (with or without backslashes). The default is the local computer. |
| /u `[<domain>]` | Runs this command with the permissions of the specified user account. By default, the command runs with the permissions of the current user of the local computer. The specified user account must be a member of the Administrators group on the remote computer. The **/u** and **/p** parameters are valid only when you use **/s**. |
| /p `<password>` | Specifies the password of the user account specified in the **/u** parameter. If you use the **/u** parameter without the **/p** parameter or the password argument, schtasks will prompt you for a password. The **/u** and **/p** parameters are valid only when you use **/s**. |
| /? | Displays help at the command prompt. |

## Examples

To stop the instance of Notepad.exe started by the *My Notepad* task, type:

```
schtasks /end /tn "My Notepad"
```

To stop the instance of Internet Explorer started by the *InternetOn* task on the remote computer, *Svr01*,type:

```
schtasks /end /tn InternetOn /s Svr01
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [schtasks change command](schtasks-change)
- [schtasks create command](schtasks-create)
- [schtasks delete command](schtasks-delete)
- [schtasks query command](schtasks-query)
- [schtasks run command](schtasks-run)