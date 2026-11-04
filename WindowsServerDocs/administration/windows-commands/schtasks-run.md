---
layout: Conceptual
title: schtasks run | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/schtasks-run
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the schtasks run command, which
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-09-16T00:00:00.0000000Z
locale: en-us
document_id: 78d0c8a9-2db2-56d4-2b9e-d5ac63e7315f
document_version_independent_id: 44a76138-a471-4a0c-ec27-70d01a948ec8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/schtasks-run.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/schtasks-run
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/schtasks-run.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 30c8e46f-b0d4-a6fb-d07e-813c801917da
---

# schtasks run | Microsoft Learn

Starts a scheduled task immediately. The run operation ignores the schedule, but uses the program file location, user account, and password saved in the task to run the task immediately. Running a task does not affect the task schedule and does not change the next run time scheduled for the task.

## Syntax

```
schtasks /run /tn <taskname> [/s <computer> [/u [<domain>\]<user> [/p <password>]]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /tn `<taskname>` | Identifies the task to start. This parameter is required. |
| /s `<computer>` | Specifies the name or IP address of a remote computer (with or without backslashes). The default is the local computer. |
| /u `[<domain>]` | Runs this command with the permissions of the specified user account. By default, the command runs with the permissions of the current user of the local computer. The specified user account must be a member of the Administrators group on the remote computer. The **/u** and **/p** parameters are valid only when you use **/s**. |
| /p `<password>` | Specifies the password of the user account specified in the **/u** parameter. If you use the **/u** parameter without the **/p** parameter or the password argument, schtasks will prompt you for a password. The **/u** and **/p** parameters are valid only when you use **/s**. |
| /? | Displays help at the command prompt. |

#### Remarks

- Use this operation to test your tasks. If a task doesn't run, check the Task Scheduler Service transaction log, `<Systemroot>\SchedLgU.txt` for errors.
- To run a task remotely, the task must be scheduled on the remote computer. When you run the task, it runs only on the remote computer. To verify that a task is running on a remote computer, use Task Manager or the Task Scheduler Service transaction log, `<Systemroot>\SchedLgU.txt`.

## Examples

To start the *Security Script* task, type:

```
schtasks /run /tn "Security Script"
```

To start the *Update* task on a remote computer, Svr01, type:

```
schtasks /run /tn Update /s Svr01
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [schtasks change command](schtasks-change)
- [schtasks create command](schtasks-create)
- [schtasks delete command](schtasks-delete)
- [schtasks end command](schtasks-end)
- [schtasks query command](schtasks-query)