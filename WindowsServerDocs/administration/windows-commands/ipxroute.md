---
layout: Conceptual
title: ipxroute | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ipxroute
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ipxroute command, which displays and modifies information about the routing tables used by the IPX protocol.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 97bec1b5-1e34-1c3a-d8da-99e3cab4bde8
document_version_independent_id: 467e7dd7-c991-643a-c44f-c179c25ce537
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ipxroute.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ipxroute
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ipxroute.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: dcb45452-9c03-1d42-c6f4-2b8162ef77bf
---

# ipxroute | Microsoft Learn

Displays and modifies information about the routing tables used by the IPX protocol. Used without parameters, **ipxroute** displays the default settings for packets that are sent to unknown, broadcast, and multicast addresses.

## Syntax

```
ipxroute servers [/type=x]
ipxroute ripout <network>
ipxroute resolve {guid | name} {GUID | <adaptername>}
ipxroute board= N [def] [gbr] [mbr] [remove=xxxxxxxxxxxx]
ipxroute config
```

### Parameters

| Parameter | Description |
| --- | --- |
| servers`[/type=x]` | Displays the Service Access Point (SAP) table for the specified server type. **x** must be an integer. For example, `/type=4` displays all file servers. If you don't specify **/type**, `ipxroute servers` displays all types of servers, listing them by server name. |
| resolve`{GUID | name}``{GUID | adaptername}` | Resolves the name of the GUID to its friendly name, or the friendly name to its GUID. |
| board= *n* | Specifies the network adapter for which to query or set parameters. |
| def | Sends packets to the ALL ROUTES broadcast. If a packet is transmitted to a unique Media Access Card (MAC) address that is not in the source routing table, **ipxroute** sends the packet to the SINGLE ROUTES broadcast by default. |
| gbr | Sends packets to the ALL ROUTES broadcast. If a packet is transmitted to the broadcast address (FFFFFFFFFFFF), **ipxroute** sends the packet to the SINGLE ROUTES broadcast by default. |
| mbr | Sends packets to the ALL ROUTES broadcast. If a packet is transmitted to a multicast address (C000xxxxxxxx), **ipxroute** sends the packet to the SINGLE ROUTES broadcast by default. |
| remove=*xxxxxxxxxxxx* | removes the given node address from the source routing table. |
| config | Displays information about all of the bindings for which IPX is configured. |
| /? | Displays help at the command prompt. |

### Examples

To display the network segments that the workstation is attached to, the workstation node address, and frame type being used, type:

```
ipxroute config
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)