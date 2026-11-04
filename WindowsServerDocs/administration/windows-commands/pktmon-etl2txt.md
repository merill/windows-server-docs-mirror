---
layout: Conceptual
title: pktmon etl2txt | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pktmon-etl2txt
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pktmon etl2txt command that provides a listing of parameters and what they do.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2021-06-24T00:00:00.0000000Z
locale: en-us
document_id: d6fa435b-0ac7-39c4-c128-9e5ba446e2da
document_version_independent_id: 3e2121e5-893c-1310-3b2e-1bdc773e3880
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pktmon-etl2txt.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pktmon-etl2txt
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pktmon-etl2txt.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4bcd2997-d85d-3be9-7468-0b55af79eb2d
---

# pktmon etl2txt | Microsoft Learn

Convert ETL log file to text format.

## Syntax

```
pktmon etl2txt <file> [--out <name>] [--stats-only] [--timestamp-only] [--metadata]
                      [--tmfpath <path>] [--brief] [--verbose <n>] [--hex]
                      [--no-ethernet] [--vxlan <port>]
```

Where `<file>` is the ETL file to convert.

### Parameters

| **Parameter** | **Description** |
| --- | --- |
| **-o, --out &lt;name&gt;** | Name of the formatted text file. |
| **-s, --stats-only** | Display log file statistical information. |
| **-t, --timestamp-only** | Use timestamp only prefix for events and packets. |
| **-m, --metadata** | Print event metadata, such as logging level and keywords. |
| **-p, --tmfpath &lt;path&gt;** | Path to TMF files for decoding WPP traces. Multiple paths should be separated by semicolons. All WPP traces are skipped when this option is not specified. |

#### Network packet formatting options

| **Parameter** | **Description** |
| --- | --- |
| **-b, --brief** | Use abbreviated packet format. |
| **-v, --verbose &lt;n&gt;** | Verbosity level from 1 to 3. |
| **-x, --hex** | Include hexadecimal format. |
| **-e, --no-ethernet** | Don't print ethernet header. |
| **-l, --vxlan &lt;port&gt;** | Custom VXLAN port. |

## Related links

- [Pktmon](pktmon)
- [Pktmon counters](pktmon-counters)
- [Pktmon etl2pcap](pktmon-etl2pcap)
- [Pktmon filter](pktmon-filter)
- [Pktmon filter add](pktmon-filter-add)
- [Pktmon hex2pkt](pktmon-hex2pkt)
- [Pktmon list](pktmon-list)
- [Pktmon reset](pktmon-reset)
- [Pktmon start](pktmon-start)
- [Pktmon status](pktmon-status)
- [Pktmon unload](pktmon-unload)
- [Packet Monitor overview](/en-us/windows-server/networking/technologies/pktmon/pktmon)