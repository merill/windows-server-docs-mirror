---
layout: Conceptual
title: pktmon filter | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pktmon-filter
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pktmon filter command that provides a listing of parameters and what they do.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2021-06-24T00:00:00.0000000Z
locale: en-us
document_id: 4be8dd43-0bee-1694-15be-404da8c66a82
document_version_independent_id: 60a6bec3-f402-5cdd-971e-84e900e1d5a0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pktmon-filter.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pktmon-filter
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pktmon-filter.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d92dfb37-c989-1ae0-d22f-0c862910eeb6
---

# pktmon filter | Microsoft Learn

Pktmon filter allows you to list, add, or remove packet filters.

## Syntax

```
pktmon filter { list | add | remove } [OPTIONS | help]
```

### Parameters

| **Parameter** | **Description** |
| --- | --- |
| **pktmon filter list** | Display active packet filters. |
| **pktmon filter add** | Add a filter to control which packets are reported. |
| **pktmon filter remove** | Remove all packet filters. |

## Related links

- [Pktmon](pktmon)
- [Pktmon counters](pktmon-counters)
- [Pktmon etl2pcap](pktmon-etl2pcap)
- [Pktmon etl2txt](pktmon-etl2txt)
- [Pktmon filter add](pktmon-filter-add)
- [Pktmon hex2pkt](pktmon-hex2pkt)
- [Pktmon list](pktmon-list)
- [Pktmon reset](pktmon-reset)
- [Pktmon start](pktmon-start)
- [Pktmon status](pktmon-status)
- [Pktmon unload](pktmon-unload)
- [Packet Monitor overview](../../networking/technologies/pktmon/pktmon)