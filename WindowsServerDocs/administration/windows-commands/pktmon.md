---
layout: Conceptual
title: pktmon | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pktmon
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pktmon network diagnostics tool for Windows that can be used for packet capture, packet drop detection, packet filtering, and counting.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2021-06-24T00:00:00.0000000Z
locale: en-us
document_id: a9c15e33-a48b-b001-09df-0e321cad3ec4
document_version_independent_id: 396ae80e-250b-ea6c-7c7e-f908bb157285
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pktmon.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pktmon
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pktmon.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 6899a1f4-4e5c-a214-31b6-f17facd92534
---

# pktmon | Microsoft Learn

Packet Monitor (Pktmon) is an in-box, cross-component network diagnostics tool for Windows. It can be used for advanced packet capture and event collection, drop detection, filtering, and counting. Pktmon is especially helpful in virtualization scenarios such as container networking and SDN, because it provides visibility within the networking stack.

## Syntax

```
pktmon { filter | list | start | stop | status | unload | counters | reset | etl2txt | etl2pcap | hex2pkt | help } [options]
```

### Commands

| **Command** | **Description** |
| --- | --- |
| [pktmon filter](pktmon-filter) | Manage packet filters. |
| [pktmon list](pktmon-list) | List packet processing components. |
| [pktmon start](pktmon-start) | Start packet capture and event collection. |
| pktmon stop | Stop data collection. |
| pktmon status | Query current status. |
| [pktmon unload](pktmon-unload) | Unload PktMon driver. |
| [pktmon counters](pktmon-counters) | Display current packet counters. |
| [pktmon reset](pktmon-reset) | Reset packet counters to zero. |
| [pktmon etl2txt](pktmon-format) | Convert log file to text format. |
| [pktmon etl2pcap](pktmon-pcapng) | Convert log file to pcapng format. |
| pktmon hex2pkt | Decode packet in hexadecimal format. |
| pktmon help | Show help text for specific command. |

## Related links

- [Packet Monitor overview](../../networking/technologies/pktmon/pktmon)
- [Pktmon support for Microsoft Network Monitor (Netmon)](../../networking/technologies/pktmon/pktmon-netmon-support)