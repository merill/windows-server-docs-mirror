---
layout: Conceptual
title: pktmon filter add | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pktmon-filter-add
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pktmon filter add command.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2021-06-24T00:00:00.0000000Z
locale: en-us
document_id: 62b31b8b-483b-0b22-7b97-b91697c78d26
document_version_independent_id: c27d6b3d-db6d-07f0-1fe1-a389f7731e46
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pktmon-filter-add.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pktmon-filter-add
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pktmon-filter-add.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 597beb9c-257f-f0d2-95a8-086183c6685d
---

# pktmon filter add | Microsoft Learn

Pktmon filter add allows you to add a filter to control which packets are reported. For a packet to be reported, it must match all conditions specified in at least one filter. Up to 32 filters can be active at once.

## Syntax

```
pktmon filter add <name> [-m <mac> [mac2]] [-v <vlan>] [-d { IPv4 | IPv6 | number }]
                         [-t { TCP [flags...] | UDP | ICMP | ICMPv6 | number }]
                         [-i <ip> [ip2]] [-p <port> [port2]] [-b] [-e [port]]
```

You may provide an optional name or description of the filter.

Note

When two MACs (-m), IPs (-i), or ports (-p) are specified, the filter matches packets that contain both. It will not distinguish between source or destination for this purpose.

### Parameters

You can supply parameters for Ethernet frame, IP header, TCP/UDP header, cluster heartbeat, and encapsulation.

| **Parameter** | **Description** |
| --- | --- |
| **-m, --mac[-address]** | Match source or destination MAC address. See note above. |
| **-v, --vlan** | Match by VLAN ID (VID) in the 802.1Q header. |
| **-d, --data-link[-protocol], --ethertype** | Match by data link (layer 2) protocol. Can be IPv4, IPv6, ARP, or a protocol number. |
| **-t, --transport[-protocol], --ip-protocol** | Match by transport (layer 4) protocol. Can be TCP, UDP, ICMP, ICMPv6, or a protocol number. To further filter TCP packets, an optional list of TCP flags to match can be provided. Supported flags are FIN, SYN, RST, PSH, ACK, URG, ECE, and CWR. |
| **-i, --ip[-address]** | Match source or destination IP address. See note above. To match by subnet, use CIDR notation with the prefix length. |
| **-p, --port** | Match source or destination port number. See note above. |
| **-b, --heartbeat** | Match RCP heartbeat messages over UDP port 3343. |
| **-e, --encap** | Apply above filtering parameters to both inner and outer encapsulation headers. Supported encapsulation methods are VXLAN, GRE, NVGRE, and IP-in-IP. Custom VXLAN port is optional, and defaults to 4789. |

## Examples

The following set of filters will capture any ICMP traffic from or to the IP address 10.0.0.10 along with any traffic on port 53.

```PowerShell
C:\Test> pktmon filter add -i 10.0.0.10 -t icmp
C:\Test> pktmon filter add -p 53
```

The following filter will capture all the SYN packets sent or received by the IP address 10.0.0.10:

```PowerShell
C:\Test> pktmon filter add -i 10.0.0.10 -t tcp syn
```

The following filter called **MyPing** pings 10.10.10.10 using the ICMP protocol:

```PowerShell
C:\Test> pktmon filter add MyPing -i 10.10.10.10 -t ICMP
```

The following filter called **MySmbSyb** captures TCP synchronized SMB traffic:

```PowerShell
C:\Test> pktmon filter add MySmbSyn -i 10.10.10.10 -t TCP SYN -p 445
```

The following filter called **MySubnet** captures traffic on the subnet mask 255.255.255.0, or /24 in CIDR notation:

```PowerShell
C:\Test> pktmon filter add MySubnet -i 10.10.10.0/24
```

## Other references

- [Pktmon](pktmon)
- [Pktmon counters](pktmon-counters)
- [Pktmon etl2pcap](pktmon-etl2pcap)
- [Pktmon etl2txt](pktmon-etl2txt)
- [Pktmon filter](pktmon-filter)
- [Pktmon hex2pkt](pktmon-hex2pkt)
- [Pktmon list](pktmon-list)
- [Pktmon reset](pktmon-reset)
- [Pktmon start](pktmon-start)
- [Pktmon status](pktmon-status)
- [Pktmon unload](pktmon-unload)
- [Packet Monitor overview](../../networking/technologies/pktmon/pktmon)