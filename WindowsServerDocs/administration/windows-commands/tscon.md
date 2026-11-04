---
layout: Conceptual
title: tscon | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tscon
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for tscon, which connects to another session on a Remote Desktop Session Host server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1d034b6f-46d2-82d6-fa32-12fc28f0fc3c
document_version_independent_id: 3458fd25-0fa3-03f0-6170-6f6904200d2c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tscon.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tscon
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tscon.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d7ef1e84-47e0-ac3c-5827-e99e116b3983
---

# tscon | Microsoft Learn

Connects to another session on a Remote Desktop Session Host server.

Important

You must have **Full Control access** permission or **Connect special access** permission to connect to another session.

Note

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
tscon {<sessionID> | <sessionname>} [/dest:<sessionname>] [/password:<pw> | /password:*] [/v]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<sessionID>` | Specifies the ID of the session to which you want to connect. If you use the optional `/dest:<sessionname>` parameter, you can also specify the name of the current session. |
| `<sessionname>` | Specifies the name of the session to which you want to connect. |
| /dest:`<sessionname>` | Specifies the name of the current session. This session will disconnect when you connect to the new session. You can also use this parameter to connect the session of another user to a different session. |
| /password:`<pw>` | Specifies the password of the user who owns the session to which you want to connect. This password is required when the connecting user does not own the session. |
| /password:`*` | Prompts for the password of the user who owns the session to which you want to connect. |
| /v | Displays information about the actions being performed. |
| /? | Displays help at the command prompt. |

#### Remarks

- This command fails if you don't specify a password in the **/password** parameter, and the target session belongs to a user other than the current one.
- You can't connect to the console session.

## Examples

To connect to *Session 12* on the current Remote Desktop Services Session Host server, and to disconnect the current session, type:

```
tscon 12
```

To connect to *Session 23* on the current Remote Desktop Services Session Host server using the password *mypass*, and to disconnect the current session, type:

```
tscon 23 /password:mypass
```

To connect the session named *TERM03* to the session named *TERM05*, and then to disconnect session *TERM05*, type:

```
tscon TERM03 /v /dest:TERM05
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)