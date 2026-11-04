---
layout: Conceptual
title: schtasks query | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/schtasks-query
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the schtasks query command, which lists all the tasks scheduled to run on the computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2024-02-13T00:00:00.0000000Z
locale: en-us
document_id: 79037345-b71f-16c5-5e52-13d009ad458e
document_version_independent_id: 77351449-bfb3-aad4-528b-fd717abc1bfa
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/schtasks-query.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/schtasks-query
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/schtasks-query.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2b5c50a9-ba98-3e23-51a9-2801f036899a
---

# schtasks query | Microsoft Learn

Lists all the tasks scheduled to run on the computer.

Syntax

```
schtasks [/query] [/fo {TABLE | LIST | CSV}] [/nh] [/v] [/s <computer> [/u [<domain>\]<user> [/p <password>]]] [/tn <taskname>] [/xml] [/hresult]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /query | Optionally, specifies the name of the operation. Using this query without any parameters performs a query of all tasks on the system. |
| /fo `<format>` | Specifies the output format. The valid values are *TABLE*, *LIST*, or *CSV*. |
| /nh | Removes column headings from the table display. This parameter is valid with the *TABLE* or *CSV* output formats. |
| /v | Adds the advanced properties of the task to the display. This parameter is valid with the *LIST* or *CSV* output formats. |
| /s `<computer>` | Specifies the name or IP address of a remote computer (with or without backslashes). The default is the local computer. |
| /u `[<domain>]` | Runs this command with the permissions of the specified user account. By default, the command runs with the permissions of the current user of the local computer. The specified user account must be a member of the Administrators group on the remote computer. The **/u** and **/p** parameters are valid only when you use **/s**. |
| /p `<password>` | Specifies the password of the user account specified in the **/u** parameter. If you use the **/u** parameter without the **/p** parameter or the password argument, schtasks will prompt you for a password. The **/u** and **/p** parameters are valid only when you use **/s**. |
| /tn `<taskname>` | Queries a specific task by path and name. If **/tn** is used, `<taskname>` cannot be blank. Assumes from root directory "*\*" folder by default (thus *\* is omittable if the task is located in the root directory). Does not accept wildcards. Use quotation marks to enclose names that include spaces. |
| /xml | Outputs all task definitions on the system to XML format. If **/tn** is specified, outputs the specific task name to XML format. The full path and name must be used. |
| /hresult | Specifies the process exit code to be in HRESULT format. |
| /? | Displays help at the command prompt. |

## Examples

To list all tasks scheduled for the local computer, type:

```
schtasks
schtasks /query
```

These commands produce the same result and can be used interchangeably.

To request a detailed display of the tasks on the local computer,type:

```
schtasks /query /fo LIST /v
```

This command uses the **/v** parameter to request a detailed (verbose) display and the **/fo LIST** parameter to format the display as a list for easy reading. You can use this command to verify that a task you created has the intended recurrence pattern.

To request a list of tasks scheduled for a remote computer and to add the tasks to a comma-separated log file on the local computer, type:

```
schtasks /query /s Reskit16 /fo csv /nh >> \\svr01\data\tasklogs\p0102.csv
```

You can use this command format to collect and track tasks that are scheduled for multiple computers. This command uses the **/s** parameter to identify the remote computer, *Reskit16*, the **/fo** parameter to specify the format and the **/nh** parameter to suppress the column headings. The **&gt;&gt;** append symbol redirects the output to the task log, *p0102.csv*, on the local computer, *Svr01*. Because the command runs on the remote computer, the local computer path must be fully qualified.

To get information for the *Office Subscription Maintenance* task using the **/tn** parameter, which can also be viewed via Task Scheduler in the location *\Microsoft\Office\* with the root directory "**\**" seen under the **Task Scheduler Library** folder, type:

```
schtasks /query /tn "\Microsoft\Office\Office Subscription Maintenance"
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [schtasks change command](schtasks-change)
- [schtasks create command](schtasks-create)
- [schtasks delete command](schtasks-delete)
- [schtasks end command](schtasks-end)
- [schtasks run command](schtasks-run)