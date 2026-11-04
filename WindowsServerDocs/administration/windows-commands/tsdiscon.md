---
layout: Conceptual
title: tsdiscon | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tsdiscon
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for tsdiscon, which disconnects a session from a Remote Desktop Session Host server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 5ea16507-e95c-554e-ee05-0b3c0ae8e13e
document_version_independent_id: d107d499-867d-34ae-9b45-ef235593a8a9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tsdiscon.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tsdiscon
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tsdiscon.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1bb60b8d-59f1-ddb7-b6ca-11958c2e64f8
---

# tsdiscon | Microsoft Learn

Disconnects a session from a Remote Desktop Session Host server. If you don't specify a session ID or session name, this command disconnects the current session.

Important

You must have **Full Control access** permission or **Disconnect special access** permission to disconnect another user from a session.

Note

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
tsdiscon [<sessionID> | <sessionname>] [/server:<servername>] [/v]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<sessionID>` | Specifies the ID of the session to disconnect. |
| `<sessionname>` | Specifies the name of the session to disconnect. |
| /server:`<servername>` | Specifies the terminal server that contains the session that you want to disconnect. Otherwise, the current Remote Desktop Session Host server is used. This parameter is required only if you run the **tsdiscon** command from a remote server. |
| /v | Displays information about the actions being performed. |
| /? | Displays help at the command prompt. |

#### Remarks

- Any applications running when you disconnected the session are automatically running when you reconnect to that session with no loss of data. You can use the [reset session command](reset-session) to end the running applications of the disconnected session, but this may result in loss of data at the session.
- The console session can't be disconnected.

## Examples

To disconnect the current session, type:

```
tsdiscon
```

To disconnect *Session 10*, type:

```
tsdiscon 10
```

To disconnect the session named *TERM04*, type:

```
tsdiscon TERM04
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)
- [reset session command](reset-session)