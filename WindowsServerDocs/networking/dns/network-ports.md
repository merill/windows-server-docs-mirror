---
layout: Conceptual
title: Network Ports Used by DNS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/dns/network-ports
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn about network ports used by DNS in Windows Server
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2025-01-27T00:00:00.0000000Z
locale: en-us
document_id: 80df9c88-7494-cece-d586-ebc094321516
document_version_independent_id: 80df9c88-7494-cece-d586-ebc094321516
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/dns/network-ports.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/dns/network-ports
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/dns/network-ports.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 0069848e-1141-89f2-f5ca-155796e4e7c2
---

# Network Ports Used by DNS | Microsoft Learn

During DNS resolution, DNS messages are sent from DNS clients to DNS servers or between DNS servers. Messages are sent over UDP and DNS servers bind to UDP port 53. When the message length exceeds the default message size for a User Datagram Protocol (UDP) datagram (512 octets), the first response to the message is sent with as much data as the UDP datagram allows. When the message size is exceeded, the DNS server sets a flag indicating a truncated response. The DNS client (message sender) can then choose to reissue the request to the DNS server using TCP (over TCP port 53). This approach takes advantage of the performance of UDP but also has a backup failover solution for longer queries.

DNS queries are typically sent from a high-numbered source port (starting at 49152 and increasing) to destination port 53. Responses are sent from source port 53 to a high-numbered destination port. The following table lists the UDP and TCP ports used for different DNS message types. To comply with Internet Assigned Numbers Authority (IANA) recommendations, the default start port is 49152, and the default end port is 65535. Using high numbered dynamic ports is a change from the configuration of versions earlier than Windows Server 2008 that used a default port range of 1025 through 5000.

| Traffic Type | Source of Transmission | Source Port | Destination of Transmission | Destination Port |
| --- | --- | --- | --- | --- |
| Queries from local DNS server | Local DNS server | A random port numbered 49152 or higher | Any remote DNS server | 53 |
| Responses to local DNS server | Any remote DNS server | 53 | Local DNS server | A random port numbered 49152 or higher |
| Queries from remote DNS server | Any remote DNS server | A random port numbered 49152 or higher | Local DNS server | 53 |
| Responses to remote DNS server | Local DNS server | 53 | Any remote DNS server | A random port numbered 49152 or higher |

The DNS Server service supports Extension Mechanisms for DNS (EDNS0), as defined in [RFC 2671](https://datatracker.ietf.org/doc/rfc2671/). EDNS0 allows DNS requestors to advertise the size of their UDP packets and facilitate the transfer of packets larger than 512 bytes. When a DNS server receives a request over UDP, it identifies the requestor’s UDP packet size from the option (OPT) resource record and scales its response to contain as many resource records as are allowed in the maximum UDP packet size specified by the requestor.

The Windows Server DNS Server supports EDNS0 and is enabled by default. It can be disabled using the registry. Locate the following registry subkey:

`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DNS\Parameters`

To disable EDNS0, add a DWORD value with the name `EnableEDNSProbes` and a value set to `0x0`.

Caution

Use extreme caution when editing the registry. Modifications to the registry aren't validated by the registry editor or by Windows before they're applied. As a result, incorrect values can be stored. Incorrect values can result in unrecoverable errors in the system.