---
layout: Conceptual
title: pktmon etl2pcap | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pktmon-etl2pcap
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pktmon etl2pcap command that provides a listing of parameters and what they do.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2021-06-24T00:00:00.0000000Z
locale: en-us
document_id: 3828f7bc-8d4e-b9d8-1559-539f0104abc2
document_version_independent_id: 5d89969c-3113-6942-ebf1-9388987ca054
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pktmon-etl2pcap.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pktmon-etl2pcap
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pktmon-etl2pcap.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
platformId: def59e05-00ef-deb8-1223-49db60eebe59
---

# pktmon etl2pcap | Microsoft Learn

Convert pktmon log file to pcapng format. Dropped packets are not included by default. These logs can be analyzed using Wireshark (or any pcapng analyzer).

## Syntax

```
pktmon etl2pcap <file> [--out <name>] [--drop-only] [--component-id <id>]
```

Where `<file>` is the ETL file to convert.

### Parameters

| **Parameter** | **Description** |
| --- | --- |
| **-o, --out &lt;name&gt;** | Name of the formatted pcapng file. |
| **-d, --drop-only** | Convert dropped packets only. |
| **-c, --component-id &lt;id&gt;** | Filter packets by a specific component ID. |

### Output filtering

All information about the packet drop reports and packet flow through the networking stack is lost in pcapng format output. Log contents should be carefully prefiltered to show the complete conversion. For example:

- Pcapng format doesn't distinguish between a flowing packet and a dropped packet. To separate all the packets in the capture from dropped packets, generate two pcapng files; one that contains all the packets (`pktmon etl2pcap log.etl --out log-capture.etl`), and another that contains only dropped packets (`pktmon etl2pcap log.etl  --drop-only --out log-drop.etl`). This way you're able to analyze the dropped packets in a separate log.
- Pcapng format doesn't distinguish between different networking components where a packet was captured. For such multilayered scenarios, specify the desired component ID in the pcapng output `pktmon etl2pcap log.etl --component-id 5`. Repeat this command for each set of component IDs that you're interested in.

## Related links

- [Pktmon](pktmon)
- [Pktmon counters](pktmon-counters)
- [Pktmon etl2txt](pktmon-etl2txt)
- [Pktmon filter](pktmon-filter)
- [Pktmon filter add](pktmon-filter-add)
- [Pktmon hex2pkt](pktmon-hex2pkt)
- [Pktmon list](pktmon-list)
- [Pktmon reset](pktmon-reset)
- [Pktmon start](pktmon-start)
- [Pktmon status](pktmon-status)
- [Pktmon unload](pktmon-unload)
- [Packet Monitor overview](/en-us/windows-server/networking/technologies/pktmon/pktmon)