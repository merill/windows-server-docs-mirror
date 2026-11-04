---
layout: Conceptual
title: pktmon hex2pkt | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pktmon-hex2pkt
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pktmon hex2pkt command that provides a listing of parameters and what they do.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2021-06-24T00:00:00.0000000Z
locale: en-us
document_id: f5af7180-cc9e-055a-fcfb-d4a56e59b5e6
document_version_independent_id: b411afd0-32ba-b0a8-6bae-1544995eb233
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pktmon-hex2pkt.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pktmon-hex2pkt
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pktmon-hex2pkt.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6ef02749-e8f3-7bae-5c3b-55d52e45fb17
---

# pktmon hex2pkt | Microsoft Learn

Decode packet in hexadecimal format.

## Syntax

```
pktmon hex2pkt [--type { Ethernet | IP | HTTP }]
```

### Parameters

| **Parameter** | **Description** |
| --- | --- |
| **-t, --type** | Packet type to decode. Options are Ethernet, IP, and HTTP. Default is Ethernet. |

## Related links

- [Pktmon](pktmon)
- [Pktmon counters](pktmon-counters)
- [Pktmon etl2pcap](pktmon-etl2pcap)
- [Pktmon etl2txt](pktmon-etl2txt)
- [Pktmon filter](pktmon-filter)
- [Pktmon filter add](pktmon-filter-add)
- [Pktmon list](pktmon-list)
- [Pktmon reset](pktmon-reset)
- [Pktmon start](pktmon-start)
- [Pktmon status](pktmon-status)
- [Pktmon unload](pktmon-unload)
- [Packet Monitor overview](/en-us/windows-server/networking/technologies/pktmon/pktmon)