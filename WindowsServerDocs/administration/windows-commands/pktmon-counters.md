---
layout: Conceptual
title: pktmon counters | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pktmon-counters
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pktmon counters command that provides a listing of parameters and what they do.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2021-06-24T00:00:00.0000000Z
locale: en-us
document_id: 97472170-ae80-c8ad-3307-cc2791b576a9
document_version_independent_id: c9fabcf4-8148-9e74-bd6a-58fd5f654cd3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pktmon-counters.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pktmon-counters
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pktmon-counters.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b8efb43d-4c04-f43b-cb05-ba04c5928153
---

# pktmon counters | Microsoft Learn

Pktmon counters allows you to query and display current packet counters from monitored components to confirm the presence of expected traffic and get a high-level view of how the traffic flowed in the machine.

## Syntax

```
pktmon counters [--type { all | flow | drop }] [--include-hidden] [--zero] [--drop-reason] [--live] [--refresh-rate <n>] [--json]
```

### Parameters

| **Parameter** | **Description** |
| --- | --- |
| **-t, --type** | Select which types of counters to show. Supported values are **all** counters (default), **flow** (flows only), or **drop** (drops only). |
| **-z, --zero** | Show counters that are zero in both directions. |
| **-i, --include-hidden** | Show counters from components that are hidden by default. |
| **-r, --drop-reason** | Show the most recent drop reason for each drop counter. |
| **--live** | Automatically refresh the counters. Press **Ctrl+C** to stop. |
| **--refresh-rate &lt;n&gt;** | Number of times to refresh the counters per second, from 1 to 30. Default is 10. |
| **--json** | Output the counters in JSON format. Implies -i and -r. |

## Related links

- [Pktmon](pktmon)
- [Pktmon etl2pcap](pktmon-etl2pcap)
- [Pktmon etl2txt](pktmon-etl2txt)
- [Pktmon filter](pktmon-filter)
- [Pktmon filter add](pktmon-filter-add)
- [Pktmon hex2pkt](pktmon-hex2pkt)
- [Pktmon list](pktmon-list)
- [Pktmon reset](pktmon-reset)
- [Pktmon start](pktmon-start)
- [Pktmon status](pktmon-status)
- [Pktmon unload](pktmon-unload)
- [Packet Monitor overview](../../networking/technologies/pktmon/pktmon)