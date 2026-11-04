---
layout: Conceptual
title: logoff | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/logoff
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the logoff command, which logs off a user from a session on a Remote Desktop Session Host server and deletes the session.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4442c721-afa5-32c6-8d9c-c20cb1e5b51d
document_version_independent_id: e715e626-c08d-3470-0899-ebcba6f85d7c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/logoff.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/logoff
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/logoff.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 7b4a73f8-7a7d-a97e-c087-165084371b7d
---

# logoff | Microsoft Learn

Logs off a user from a session on a Remote Desktop Session Host server and deletes the session.

## Syntax

```
logoff [<sessionname> | <sessionID>] [/server:<servername>] [/v]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<sessionname>` | Specifies the name of the session. This must be an active session. |
| `<sessionID>` | Specifies the numeric ID which identifies the session to the server. |
| /server:`<servername>` | Specifies the Remote Desktop Session Host server that contains the session whose user you want to log off. If unspecified, the server on which you are currently active is used. |
| /v | Displays information about the actions being performed. |
| /? | Displays help at the command prompt. |

#### Remarks

- You can always log off yourself from the session to which you are currently logged on. You must, however, have **Full Control** permission to log off users from other sessions.
- Logging off a user from a session without warning can result in loss of data at the user's session. You should send a message to the user by using the **msg** command to warn the user before taking this action.
- If `<sessionID>` or `<sessionname>` isn't specified, **logoff** logs the user off from the current session.
- After you log off a user, all processes end and the session is deleted from the server.
- You can't log off a user from the console session.

### Examples

To log off a user from the current session, type:

```
logoff
```

To log off a user from a session by using the session's ID, for example *session 12*, type:

```
logoff 12
```

To log off a user from a session by using the name of the session and server, for example session *TERM04* on *Server1*, type:

```
logoff TERM04 /server:Server1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)