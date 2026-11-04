---
layout: Conceptual
title: shadow | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/shadow
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the shadow command, which enables you to remotely control an active session of another user on a Remote Desktop Session Host server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 74532375-ec3e-cc3b-4b0e-6deb32c7f3ec
document_version_independent_id: 5f384a72-0aac-0c29-a30a-119c311a02ed
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/shadow.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/shadow
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/shadow.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 581bd5cb-c127-2918-9b8b-33f1d6b586d3
---

# shadow | Microsoft Learn

Enables you to remotely control an active session of another user on a Remote Desktop Session Host server.

## Syntax

```
shadow {<sessionname> | <sessionID>} [/server:<servername>] [/v]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<sessionname>` | Specifies the name of the session that you want to remotely control. |
| `<sessionID>` | Specifies the ID of the session that you want to remotely control. Use **query user** to display the list of sessions and their session IDs. |
| /server:`<servername>` | Specifies the Remote Desktop Session Host server containing the session that you want to remotely control. By default, the current Remote Desktop Session Host4 server is used. |
| /v | Displays information about the actions being performed. |
| /? | Displays help at the command prompt. |

#### Remarks

- You can either view or actively control the session. If you choose to actively control a user's session, you will be able to input keyboard and mouse actions to the session.
- You can always remotely control your own sessions (except the current session), but you must have Full Control permission or remote Control special access permission to remotely control another session.
- You can also initiate remote control by using Remote Desktop Services Manager.
- Before monitoring begins, the server warns the user that the session is about to be remotely controlled, unless this warning is disabled. Your session might appear to be frozen for a few seconds while it waits for a response from the user. To configure remote control for users and sessions, use the Remote Desktop Services Configuration tool or the Remote Desktop Services extensions to Local Users and Groups and active directory Users and computers.
- Your session must be capable of supporting the video resolution used at the session that you are remotely controlling or the operation fails.
- The console session can neither remotely control another session nor can it be remotely controlled by another session.
- When you want to end remote control (shadowing), press CTRL+`*` (by using `*` from the numeric keypad only).

## Examples

To shadow *session 93*, type:

```
shadow 93
```

To shadow the session *ACCTG01*, type:

```
shadow ACCTG01
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)