---
layout: Conceptual
title: change logon | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/change-logon
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the change logon command, which enables or disables logons from client sessions, or displays current logon status.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c27590c6-eea8-a53c-987c-ebbdccdde812
document_version_independent_id: f7780ce8-8796-ce4b-401a-e0543e7c7da4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/change-logon.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/change-logon
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/change-logon.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 08bf93b6-63ab-77cc-99dc-57622f8d54f4
---

# change logon | Microsoft Learn

Enables or disables logons from client sessions, or displays current logon status. This utility is useful for system maintenance. You must be an administrator to run this command.

Note

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
change logon {/query | /enable | /disable | /drain | /drainuntilrestart}
```

### Parameters

| Parameter | Description |
| --- | --- |
| /query | Displays the current logon status, whether enabled or disabled. |
| /enable | Enables logons from client sessions, but not from the console. |
| /disable | Disables subsequent logons from client sessions, but not from the console. Does not affect currently logged on users. |
| /drain | Disables logons from new client sessions, but allows reconnections to existing sessions. |
| /drainuntilrestart | Disables logons from new client sessions until the computer is restarted, but allows reconnections to existing sessions. |
| /? | Displays help at the command prompt. |

#### Remarks

- Logons are re-enabled when you restart the system.
- If you're connected to the Remote Desktop Session Host server from a client session, and then you disable logons and log off before re-enabling logons, you won't be able to reconnect to your session. To re-enable logons from client sessions, log on at the console.

### Examples

- To display the current logon status, type:

    ```
    change logon /query
    ```
- To enable logons from client sessions, type:

    ```
    change logon /enable
    ```
- To disable client logons, type:

    ```
    change logon /disable
    ```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [change command](change)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)