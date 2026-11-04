---
layout: Conceptual
title: query process | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/query-process
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the query process command, which displays information about processes that are running on a Remote Desktop Session Host server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 511f8e77-81c5-9565-22d6-4f2ed28591cd
document_version_independent_id: 3dfc7da6-088a-12fc-bb60-bf25183ca9b6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/query-process.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/query-process
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/query-process.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0ba601be-7f39-e1cc-24ec-02b6e854e70c
---

# query process | Microsoft Learn

Displays information about processes that are running on a Remote Desktop Session Host server. You can use this command to find out which programs a specific user is running, and also which users are running a specific program. This command returns the following information:

- User who owns the process
- Session that owns the process
- ID of the session
- Name of the process
- ID of the process

Note

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
query process [*|<processID>|<username>|<sessionname>|/id:<nn>|<programname>] [/server:<servername>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| \* | Lists the processes for all sessions. |
| `<processID>` | Specifies the numeric ID identifying the process that you want to query. |
| `<username>` | Specifies the name of the user whose processes you want to list. |
| `<sessionname>` | Specifies the name of the active session whose processes you want to list. |
| /id:`<nn>` | Specifies the ID of the session whose processes you want to list. |
| `<programname>` | Specifies the name of the program whose processes you want to query. The .exe extension is required. |
| /server:`<servername>` | Specifies the Remote Desktop Session Host server whose processes you want to list. If unspecified, the server where you are currently logged on is used. |
| /? | Displays help at the command prompt. |

#### Remarks

- Administrators have full access to all **query process** functions.
- If you don't specify the &lt;*username*&gt;, &lt;*sessionname*&gt;, */id:`<nn>`*, &lt;*programname*&gt;, or *\** parameters, this query displays only the processes that belong to the current user.
- When **query process** returns information, a greater than `(>)` symbol is displayed before each process that belongs to the current session.

## Examples

To display information about the processes being used by all sessions, type:

```
query process *
```

To display information about the processes being used by *session ID 2*, type:

```
query process /ID:2
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [query command](query)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)