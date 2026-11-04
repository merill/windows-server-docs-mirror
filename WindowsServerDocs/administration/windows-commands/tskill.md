---
layout: Conceptual
title: tskill | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tskill
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tskill command, which ends a process running in a session on a Remote Desktop Session Host server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 56acf2c9-0faf-82d1-970f-b5dca4c40b34
document_version_independent_id: a6976176-dad5-ba8b-9a3b-9438794934a5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tskill.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tskill
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tskill.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4cde602f-e065-3f37-7af6-422a1fcd7efc
---

# tskill | Microsoft Learn

Ends a process running in a session on a Remote Desktop Session Host server.

Note

You can use this command to end only those processes that belong to you, unless you are an administrator. Administrators have full access to all **tskill** functions and can end processes that are running in other user sessions.

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
tskill {<processID> | <processname>} [/server:<servername>] [/id:<sessionID> | /a] [/v]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<processID>` | Specifies the ID of the process that you want to end. |
| `<processname>` | Specifies the name of the process that you want to end. This parameter can include wildcard characters. |
| /server:`<servername>` | Specifies the terminal server that contains the process that you want to end. If **/server** isn't specified, the current Remote Desktop Session Host server is used. |
| /id:`<sessionID>` | Ends the process that is running in the specified session. |
| /a | Ends the process that is running in all sessions. |
| /v | Displays information about the actions being performed. |
| /? | Displays help at the command prompt. |

#### Remarks

- When all processes that are running in a session end, the session also ends.
- If you use the `<processname>` and the `/server:<servername>` parameters, you must also specify either the `/id:<sessionID>` or the **/a** parameter.

## Examples

To end process 6543, type:

```
tskill 6543
```

To end the process explorer running on session 5, type:

```
tskill explorer /id:5
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)