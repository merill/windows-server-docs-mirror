---
layout: Conceptual
title: query termserver | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/query-termserver
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the query termserver command, which displays a list of all Remote Desktop Session Host servers on the network.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e44e8a36-32a8-3aba-bdeb-de7c168a4237
document_version_independent_id: 89d21dea-3f36-0971-9b82-1aa108cd4fc3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/query-termserver.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/query-termserver
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/query-termserver.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 14d699ae-9e42-99ff-fca3-b2e84cdd9c19
---

# query termserver | Microsoft Learn

Displays a list of all Remote Desktop Session Host servers on the network. This command searches the network for all attached Remote Desktop Session Host servers and returns the following information:

- Name of the server
- Network (and node address if the /address option is used)

Note

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
query termserver [<servername>] [/domain:<domain>] [/address] [/continue]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<servername>` | Specifies the name that identifies the Remote Desktop Session Host server. |
| /domain:`<domain>` | Specifies the domain to query for terminal servers. You don't need to specify a domain if you are querying the domain in which you are currently working. |
| /address | Displays the network and node addresses for each server. |
| /continue | Prevents pausing after each screen of information is displayed. |
| /? | Displays help at the command prompt. |

### Examples

To display information about all Remote Desktop Session Host servers on the network, type:

```
query termserver
```

To display information about the Remote Desktop Session Host server named *Server3*, type:

```
query termserver Server3
```

To display information about all Remote Desktop Session Host servers in domain *CONTOSO*, type:

```
query termserver /domain:CONTOSO
```

To display the network and node address for the Remote Desktop Session Host server named *Server3*, type:

```
query termserver Server3 /address
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [query command](query)
- [Remote Desktop Services (Terminal Services) Command Reference](remote-desktop-services-terminal-services-command-reference)