---
layout: Conceptual
title: pktmon unload | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pktmon-unload
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pktmon unload command that provides a listing of parameters and what they do.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2021-06-24T00:00:00.0000000Z
locale: en-us
document_id: 58c50c2a-03f8-1309-306b-551861bdc3e1
document_version_independent_id: 252ab3eb-f52d-c378-b6db-e72d830d44be
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pktmon-unload.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pktmon-unload
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pktmon-unload.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 329ffe56-28db-b654-a931-c7a673c29f70
---

# pktmon unload | Microsoft Learn

Stop the PktMon driver service and unload PktMon.sys. Effectively equivalent to 'sc.exe stop PktMon'. Measurement (if active) will immediately stop, and any state will be deleted (counters, filters, etc.).

## Syntax

```
pktmon unload
```

## Related links

- [Pktmon](pktmon)
- [Pktmon counters](pktmon-counters)
- [Pktmon etl2pcap](pktmon-etl2pcap)
- [Pktmon etl2txt](pktmon-etl2txt)
- [Pktmon filter](pktmon-filter)
- [Pktmon filter add](pktmon-filter-add)
- [Pktmon hex2pkt](pktmon-hex2pkt)
- [Pktmon list](pktmon-list)
- [Pktmon reset](pktmon-reset)
- [Pktmon start](pktmon-start)
- [Pktmon status](pktmon-status)
- [Packet Monitor overview](../../networking/technologies/pktmon/pktmon)