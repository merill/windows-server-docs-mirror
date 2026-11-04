---
layout: Conceptual
title: schtasks commands | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/schtasks
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the schtasks commands, which schedules commands and programs to run periodically or at a specific time, adds and removes tasks from the schedule, starts and stops tasks on demand, and displays and changes scheduled tasks.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-02-01T00:00:00.0000000Z
locale: en-us
document_id: 017089b7-e7fe-f1d8-854f-91d1619164b6
document_version_independent_id: 766063ce-6e31-fa5f-da41-27b75ecec05d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/schtasks.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/schtasks
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/schtasks.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9f548d50-22d0-f4db-9e74-c85b83bf75ac
---

# schtasks commands | Microsoft Learn

Schedules commands and programs to run periodically or at a specific time, adds and removes tasks from the schedule, starts and stops tasks on demand, and displays and changes scheduled tasks.

Note

The **schtasks.exe** tool performs the same operations as **Scheduled Tasks** in **Control Panel**. You can use these tools together and interchangeably.

## Required permissions

- To schedule, view, and change all tasks on the local computer, you must be a member of the Administrators group.
- To schedule, view, and change all tasks on the remote computer, you must be a member of the Administrators group on the remote computer, or you must use the **/u** parameter to provide the credentials of an Administrator of the remote computer.
- You can use the **/u** parameter in a **/create** or **/change** operation if the local and remote computers are in the same domain, or if the local computer is in a domain that the remote computer domain trusts. Otherwise, the remote computer can't authenticate the user account specified, and it can't verify that the account is a member of the Administrators group.
- The task you plan to run must have the appropriate permission; these permissions vary by task. By default, tasks run with the permissions of the current user of the local computer, or with the permissions of the user specified by the **/u** parameter, if one is included. To run a task with permissions of a different user account or with system permissions, use the **/ru** parameter.

## Syntax

```
schtasks /change
schtasks /create
schtasks /delete
schtasks /end
schtasks /query
schtasks /run
```

### Parameters

| Parameter | Description |
| --- | --- |
| [schtasks change](schtasks-change) | Changes one or more of the following properties of a task:<br>- The program that the task runs (/tr)<br>- The user account under which the task runs (/ru)<br>- The password for the user account (/rp)<br>- Adds the interactive-only property to the task (/it) |
| [schtasks create](schtasks-create) | Schedules a new task. |
| [schtasks delete](schtasks-delete) | Deletes a scheduled task. |
| [schtasks end](schtasks-end) | Stops a program started by a task. |
| [schtasks query](schtasks-query) | Displays tasks scheduled to run on the computer. |
| [schtasks run](schtasks-run) | Starts a scheduled task immediately. The **run** operation ignores the schedule, but uses the program file location, user account, and password saved in the task to run the task immediately. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)