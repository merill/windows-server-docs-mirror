---
layout: Conceptual
title: query user | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/query-user
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the query user command, which displays information about user sessions on a Remote Desktop Session Host server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4956805f-723a-7323-ed51-c8a5b1299ebc
document_version_independent_id: 86514c11-21e4-5bb3-7845-b09451d36963
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/query-user.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/query-user
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/query-user.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 12353496-6aff-4814-e950-98c26e3ada74
---

# query user | Microsoft Learn

Displays information about user sessions on a Remote Desktop Session Host server. You can use this command to find out if a specific user is logged on to a specific Remote Desktop Session Host server. This command returns the following information:

- Name of the user
- Name of the session on the Remote Desktop Session Host server
- Session ID
- State of the session (active or disconnected)
- Idle time (the number of minutes since the last keystroke or mouse movement at the session)
- Date and time the user logged on

Note

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
query user [<username> | <sessionname> | <sessionID>] [/server:<servername>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<username>` | Specifies the logon name of the user that you want to query. |
| `<sessionname>` | Specifies the name of the session that you want to query. |
| `<sessionID>` | Specifies the ID of the session that you want to query. |
| /server:`<servername>` | Specifies the Remote Desktop Session Host server that you want to query. Otherwise, the current Remote Desktop Session Host server is used. This parameter is only required if you're using this command from a remote server. |
| /? | Displays help at the command prompt. |

#### Remarks

- To use this command, you must have Full Control permission or special access permission.
- If you don't specify a user using the &lt;*username*&gt;, &lt;*sessionname*&gt;, or *sessionID* parameters, a list of all users who are logged on to the server is returned. Alternatively, you can also use the **query session** command to display a list of all sessions on a server.
- When **query user** returns information, a greater than `(>)` symbol is displayed before the current session.

### Examples

To display information about all users logged on the system, type:

```
query user
```

To display information about the user *USER1* on server *Server1*, type:

```
query user USER1 /server:Server1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [query command](query)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)