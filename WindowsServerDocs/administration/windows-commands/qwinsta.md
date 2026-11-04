---
layout: Conceptual
title: qwinsta | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/qwinsta
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the qwinsta command, which displays information about sessions on a Remote Desktop Session Host server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7edd4ef6-0753-2c32-0adb-d6326559c856
document_version_independent_id: f55fa3f6-9030-9f46-5589-0cc39e41e5d0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/qwinsta.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/qwinsta
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/qwinsta.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ac390687-1f12-07b5-4eb5-bc6f4dcc45d6
---

# qwinsta | Microsoft Learn

Displays information about sessions on a Remote Desktop Session Host server. The list includes information not only about active sessions but also about other sessions that the server runs.

Note

This command is the same as the [query session command](query-session). To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
qwinsta [<sessionname> | <username> | <sessionID>] [/server:<servername>] [/mode] [/flow] [/connect] [/counter]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<sessionname>` | Specifies the name of the session that you want to query. |
| `<username>` | Specifies the name of the user whose sessions you want to query. |
| `<sessionID>` | Specifies the ID of the session that you want to query. |
| /server:`<servername>` | Identifies the rd Session Host server to query. The default is the current server. |
| /mode | Displays current line settings. |
| /flow | Displays current flow-control settings. |
| /connect | Displays current connect settings. |
| /counter | Displays current counters information, including the total number of sessions created, disconnected, and reconnected. |
| /? | Displays help at the command prompt. |

#### Remarks

- A user can always query the session to which the user is currently logged on. To query other sessions, the user must have special access permission.
- If you don't specify a session using the &lt;*username*&gt;, &lt;*sessionname*&gt;, or *sessionID* parameters, this query will display information about all active sessions in the system.
- When **qwinsta** returns information, a greater than `(>)` symbol is displayed before the current session. For example:

    ```
    C:\>qwinsta
        SESSIONNAME     USERNAME        ID STATE    TYPE    DEVICE
        console         Administrator1  0 active    wdcon
        >rdp-tcp#1      User1           1 active    wdtshare
        rdp-tcp                         2 listen    wdtshare
                                        4 idle
                                        5 idle
    ```

    Where:

    - **SESSIONNAME** specifies the name assigned to the session.
    - **USERNAME** indicates the user name of the user connected to the session.
    - **STATE** provides information about the current state of the session.
    - **TYPE** indicates the session type.
    - **DEVICE**, which isn't present for the console or network-connected sessions, is the device name assigned to the session.
    - Any sessions in which the initial state is configured as DISABLED won't show up in the **qwinsta** list until they're enabled.

### Examples

To display information about all active sessions on server *Server2*, type:

```
qwinsta /server:Server2
```

To display information about active session *modeM02*, type:

```
qwinsta modeM02
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [query session command](query-session)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)