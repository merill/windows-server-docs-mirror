---
layout: Conceptual
title: DNS Encryption using DNS over HTTPS in Windows and Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/dns/dns-encryption-dns-over-https
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Discover how DNS over HTTPS (DoH) in Windows enhances privacy and security by encrypting DNS queries and responses using HTTPS and TLS.
author: robinharwood
ms.author: roharwoo
ms.reviewer: canasjorge
ms.topic: concept-article
ms.date: 2026-02-12T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 4bd2aac9-5250-9540-578f-b6ef66642259
document_version_independent_id: 4bd2aac9-5250-9540-578f-b6ef66642259
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/dns/dns-encryption-dns-over-https.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/dns/dns-encryption-dns-over-https
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/dns/dns-encryption-dns-over-https.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 4a9ca1c1-4110-80e9-99f5-55eb1ae37c33
---

# DNS Encryption using DNS over HTTPS in Windows and Windows Server | Microsoft Learn

Traditional DNS uses unencrypted UDP or TCP messages on port 53, which exposes DNS traffic to passive monitoring, traffic analysis, and active manipulation by attackers. DNS encryption protects DNS query and response traffic from being observed, modified, or tampered with while in transit over a network.

DNS over HTTPS (DoH) is a standards‑based mechanism that encrypts DNS traffic by encapsulating DNS messages within HTTPS, providing confidentiality and integrity using Transport Layer Security (TLS). By encrypting DNS traffic, DoH helps prevent eavesdropping, man‑in‑the‑middle attacks, and unauthorized inspection of DNS queries and responses.

## How DNS over HTTPS works

DNS over HTTPS doesn't change the fundamental DNS query and response model. Instead, it changes how DNS messages are transported across the network. When you enable DoH on a DNS Server, DoH becomes an additional encrypted communication option, and the DNS Server continues to answer traditional DNS queries unless you explicitly disable that capability.

When you enable DoH:

- The DNS server listens to HTTPS traffic.
- You configure a [DoH-capable client (such as a Windows 11 client)](doh-client-support) to use encrypted queries to a DNS server.
- The DoH client establishes a TLS connection to the DNS server.
- The client sends DNS queries inside an HTTPS request.
- The DNS server processes the query as usual.
- The DNS response is returned inside the HTTPS response.

## DNS over HTTPS for DNS Server

Starting with the 2026-06 Security Update ([KB5094125](https://support.microsoft.com/help/5094125)) for Windows Server 2025, you can enable DNS over HTTPS (DoH) on the DNS Server service to encrypt DNS traffic between DoH-capable clients and your DNS server.

An example of the DoH communication flow is as shown in the following diagram.

[![Diagram that shows the DNS over HTTPS communication flow between a client and server.](../media/dns-encryption-dns-over-https/overview.png)](../media/dns-encryption-dns-over-https/overview.png#lightbox)

When you configure DNS over HTTPS for DNS Server, consider the following points:

- Upstream DNS communication (forwarders, conditional forwarders, authoritative servers) remains unencrypted.
- DNS zone transfers remain unencrypted.
- DNS dynamic updates remain unencrypted by default.
- You can't create a DNS query filter that only matches DoH queries.
- Policies with a Transport Protocol query filter don't match DoH queries. For example, a policy with Transport Protocol filter set to `EQ, TCP` doesn't match DoH.

## Security benefits of DNS over HTTPS

DNS over HTTPS provides the following security and privacy benefits:

- **Confidentiality**. DNS queries and responses are encrypted, preventing passive monitoring.
- **Integrity**. TLS protects DNS messages from modification during transit.
- **Authentication**. DNS clients can validate the identity of the DNS server using standard HTTPS certificate validation.
- **Resistance to traffic analysis**. DNS traffic blends with other HTTPS traffic, reducing exposure to DNS‑specific filtering or manipulation. This approach improves privacy and resistance to interception.

## DNS over HTTPS protocols and standards

The IETF defines DNS over HTTPS in [RFC 8484 – DNS Queries over HTTPS (DoH)](https://www.rfc-editor.org/rfc/rfc8484.txt).

RFC 8484 specifies how to send and receive DNS messages using HTTP over TLS. The DoH standard supports both GET and POST methods and defines media types for DNS messages. This approach allows DNS traffic to benefit from modern HTTPS features such as encryption, authentication, and connection reuse.

Additionally, the DoH standard allows server implementations the freedom to configure the server’s listening URI and port, enabling flexible deployment across different network environments.

## DNS encryption and DNSSEC

DNS encryption, such as DoH, and DNSSEC address different threat models and are complementary technologies. DNS encryption protects DNS traffic on the wire, while DNSSEC ensures that DNS data is cryptographically verified for integrity and comes from an authoritative source.

By using DoH together with DNSSEC, you get defense in depth by combining encrypted transport with authenticated DNS data. For more information about DNSSEC, see [What is DNSSEC?](dnssec-overview)