---
layout: Conceptual
title: reset session | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reset-session
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for reset session command, which enables you to reset a session on a Remote Desktop Session Host server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: aac0c91a-f8f2-8bea-242b-bf0d87fb78e4
document_version_independent_id: 3c2d8efc-622e-399a-30d9-b59a7289c190
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reset-session.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reset-session
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reset-session.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f9a4dcca-3eb6-1cc5-8b24-03d35f0b7039
---

# reset session | Microsoft Learn

Enables you to reset (delete) a session on a Remote Desktop Session Host server. You should reset a session only when it malfunctions or appears to have stopped responding.

Note

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
reset session {<sessionname> | <sessionID>} [/server:<servername>] [/v]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<sessionname>` | Specifies the name of the session that you want to reset. To determine the name of the session, use the [query session command](query-session). |
| `<sessionID>` | Specifies the ID of the session to reset. |
| /server:`<servername>` | Specifies the terminal server containing the session that you want to reset. Otherwise, it uses the current Remote Desktop Session Host server. This parameter is required only if you use this command from a remote server. |
| /v | Displays information about the actions being performed. |
| /? | Displays help at the command prompt. |

### Remarks

- You can always reset your own sessions, but you must have **Full Control** access permission to reset another user's session. Be aware that resetting a user's session without warning the user can result in the loss of data at the session.

## Examples

To reset the session designated *rdp-tcp#6*, type:

```
reset session rdp-tcp#6
```

To reset the session that uses *session ID 3*, type:

```
reset session 3
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Remote Desktop Services Command Reference](remote-desktop-services-terminal-services-command-reference)