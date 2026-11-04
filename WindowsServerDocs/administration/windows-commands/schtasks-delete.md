---
layout: Conceptual
title: schtasks delete | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/schtasks-delete
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the schtasks delete command, which deletes a scheduled task from the schedule.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-09-16T00:00:00.0000000Z
locale: en-us
document_id: 91fc2176-5340-0aaa-a548-92329b3c4f19
document_version_independent_id: 4971f5d5-602f-8c94-970e-739eb8eac969
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/schtasks-delete.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/schtasks-delete
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/schtasks-delete.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 02909e7c-10f7-5583-1390-5f0c16b202c0
---

# schtasks delete | Microsoft Learn

Deletes a scheduled task from the schedule. This command doesn't delete the program that the task runs or interrupt a running program.

## Syntax

```
schtasks /delete /tn {<taskname> | *} [/f] [/s <computer> [/u [<domain>\]<user> [/p <password>]]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /tn `{<taskname> | *}` | Identifies the task to be deleted. If you use the `*`, this command deletes all tasks scheduled for the computer, not just the tasks scheduled by the current user. |
| /f | Suppresses the confirmation message. The task is deleted without warning. |
| /s `<computer>` | Specifies the name or IP address of a remote computer (with or without backslashes). The default is the local computer. |
| /u `[<domain>]` | Runs this command with the permissions of the specified user account. By default, the command runs with the permissions of the current user of the local computer. The specified user account must be a member of the Administrators group on the remote computer. The **/u** and **/p** parameters are valid only when you use **/s**. |
| /p `<password>` | Specifies the password of the user account specified in the **/u** parameter. If you use the **/u** parameter without the **/p** parameter or the password argument, schtasks will prompt you for a password. The **/u** and **/p** parameters are valid only when you use **/s**. |
| /? | Displays help at the command prompt. |

## Examples

To delete the *Start Mail* task from the schedule of a remote computer.

```
schtasks /delete /tn "Start Mail" /s Svr16
```

This command uses the **/s** parameter to identify the remote computer.

To delete all tasks from the schedule of the local computer, including tasks scheduled by other users.

```
schtasks /delete /tn * /f
```

This command uses the **/tn \*** parameter to represent all tasks on the computer and the **/f** parameter to suppress the confirmation message.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [schtasks change command](schtasks-change)
- [schtasks create command](schtasks-create)
- [schtasks end command](schtasks-end)
- [schtasks query command](schtasks-query)
- [schtasks run command](schtasks-run)