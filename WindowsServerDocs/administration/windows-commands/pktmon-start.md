---
layout: Conceptual
title: pktmon start | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pktmon-start
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pktmon start command that provides a listing of parameters and what they do.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2021-06-24T00:00:00.0000000Z
locale: en-us
document_id: 40356cb6-003a-4a62-bdb2-4bbb16ba22d0
document_version_independent_id: 4c2aa8c4-bf0f-32e8-52d2-28accf8a43a3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pktmon-start.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pktmon-start
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pktmon-start.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: cc2a8d4c-9913-694f-bfe2-35f14d93d906
---

# pktmon start | Microsoft Learn

Starts packet capture and event collection.

## Syntax

```
pktmon start [--capture [--counters-only] [--comp <selector>] [--type <type>] [--pkt-size <bytes>] [--flags <mask>]]
             [--trace --provider <name> [--keywords <k>] [--level <n>] ...]
             [--file-name <name>] [--file-size <size>] [--log-mode <mode>]
```

### Packet capture parameters

Use **-c** or **--capture** to enable packet capture and packet counters, along with the following optional parameters.

| **Parameter** | **Description** |
| --- | --- |
| **-o, --counters-only** | Collect packet counters only. No packet logging. |
| **--comp** | Select components to capture packets on. Can be all components (all), NICs only (nics), or a list of component IDs. Defaults to all. |
| **--type** | Select which packets to capture. Can be all, flow, or drop. Default is all. |
| **--pkt-size &lt;bytes&gt;** | Number of bytes to log from each packet. To always log the entire packet, set this to 0. Default is 128 bytes. |
| **--flags &lt;mask&gt;** | Hexadecimal bitmask that controls information logged during packet capture. Default is 0x012. Packet capture flags, below. |

#### Packet capture flags

The following flags apply to the **--flags** parameter (see above).

| **Flag** | **Description** |
| --- | --- |
| **0x001** | Internal Packet Monitor errors. |
| **0x002** | Information about components, counters, and filters. This information is added to the end of the log file. |
| **0x004** | Source and destination information for the first packet in NET\_BUFFER\_LIST group. |
| **0x008** | Select packet metadata from NDIS\_NET\_BUFFER\_LIST\_INFO enumeration. |
| **0x010** | Raw packet, truncated to the size specified in the [--pkt-size] parameter. |

### Event collection parameters

Use **-t** or **--trace** to enable event collection, along with the following optional parameters.

| **Parameter** | **Description** |
| --- | --- |
| **-p, --provider &lt;name&gt;** | Event provider name or GUID. For multiple providers, use this parameter more than once. |
| **-k, --keywords &lt;k&gt;** | Hexadecimal bitmask that controls which events are logged for the corresponding provider. Default is 0xFFFFFFFF. |
| **-l, --level &lt;n&gt;** | Logging level for the corresponding provider. Default is 4 (info level). |

### Logging parameters

Use the following parameters for logging:

| **Parameter** | **Description** |
| --- | --- |
| **-f, --file-name &lt;name&gt;** | Log file name. Default is PktMon.etl. |
| **-s, --file-size &lt;size&gt;** | Maximum log file size in megabytes. Default is 512 MB. |
| **-m, --log-mode** | Sets the logging mode (see below). Default is circular. |

#### Logging modes

The following modes apply to the **-m** or **--log-mode** parameter (see above).

| **Mode** | **Description** |
| --- | --- |
| **circular** | New events overwrite the oldest ones when the log is full. |
| **multi-file** | A new log file is created each time the log is full. Log files are sequentially numbered: PktMon1.etl, PktMon2.etl, etc. No limited on the number of captured events. |
| **real-time** | Display events and packets on screen at real time. No log file is created. Press **Ctrl+C** to stop monitoring. |
| **memory** | Like circular, but the entire log is stored in memory. It is written to a file when pktmon is stopped. Memory buffer size is specified in [--file-size] parameter. |

## Examples

**Example 1: Packet capture**

```PowerShell
C:\Test> pktmon start --capture
```

**Example 2: Packet counters only**

```PowerShell
C:\Test> pktmon start --capture --counters-only
```

**Example 3: Event logging**

```PowerShell
C:\Test> pktmon start --trace -p Microsoft-Windows-TCPIP -p Microsoft-Windows-NDIS
```

**Example 4: Packet capture with event logging**

```PowerShell
C:\Test> pktmon start --capture --trace -p Microsoft-Windows-TCPIP -k 0xFF -l 4
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
- [Pktmon status](pktmon-status)
- [Pktmon unload](pktmon-unload)
- [Packet Monitor overview](../../networking/technologies/pktmon/pktmon)