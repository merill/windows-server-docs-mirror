---
layout: Conceptual
title: Transport Layer Security protocol | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/tls/transport-layer-security-protocol
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
ms.author: roharwoo
author: Andrei-Popov
description: Learn about how the Transport Layer Security (TLS) protocol works and provides links to the IETF RFCs for TLS 1.0, TLS 1.1, and TLS 1.2.
ms.topic: concept-article
ms.date: 2023-07-31T00:00:00.0000000Z
locale: en-us
document_id: 674208bc-fe92-8cc3-1161-4b03dbc413c8
document_version_independent_id: fea49931-618b-cd10-0b8e-69de1ed330d6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/tls/transport-layer-security-protocol.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/tls/transport-layer-security-protocol
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/tls/transport-layer-security-protocol.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f68be8bc-f76d-1c5d-7450-5e6c3282ed35
---

# Transport Layer Security protocol | Microsoft Learn

This topic for the IT professional describes how the Transport Layer Security (TLS) protocol works and provides links to the IETF RFCs for TLS 1.0, TLS 1.1, and TLS 1.2.

Note

In a future release of Windows Server, TLS 1.0 and 1.1 will be disabled by default. For more information, see [TLS versions 1.0 and 1.1 disablement resources](/en-us/windows/whats-new/deprecated-features-resources).

The TLS (and SSL) protocols are located between the application protocol layer and the TCP/IP layer, where they can secure and send application data to the transport layer. Because the protocols work between the application layer and the transport layer, TLS and SSL can support multiple application layer protocols.

TLS and SSL assume that a connection-oriented transport, typically TCP, is in use. The protocol allows client and server applications to detect the following security risks:

- Message tampering
- Message interception
- Message forgery

The TLS and SSL protocols can be divided into two layers. The first layer consists of the application protocol and the three handshaking protocols: the handshake protocol, the change cipher spec protocol, and the alert protocol. The second layer is the record protocol.

**TLS and SSL protocol layers**

The Schannel SSP implements the TLS and SSL protocols without modification. The SSL protocol is proprietary, but the Internet Engineering Task Force produces the public TLS specifications. For information about which TLS or SSL version is supported in Windows versions, see [Protocols in TLS/SSL (Schannel SSP)](/en-us/windows/win32/secauthn/protocols-in-tls-ssl--schannel-ssp-). Each specification contains information about:

- The TLS Record Protocol
- The TLS Handshaking Protocols: - Change cipher spec protocol - Alert protocol
- Cryptographic Computations
- Mandatory Cipher Suites
- Application Data Protocol

[RFC 5246 - The Transport Layer Security (TLS) Protocol Version 1.2](http://tools.ietf.org/html/rfc5246)

[RFC 4346 - The Transport Layer Security (TLS) Protocol Version 1.1](http://tools.ietf.org/html/rfc4346)

[RFC 2246 - The TLS Protocol Version 1.0](http://tools.ietf.org/html/rfc2246)

## TLS session resumption

Introduced in Windows Server 2012 R2 , the Schannel SSP implemented the server-side portion of TLS session resumption. The client-side implementation of RFC 5077 was added in Windows 8.

Devices that connect TLS to servers frequently need to reconnect. TLS session resumption reduces the cost of establishing TLS connections because resumption involves an abbreviated TLS handshake. This facilitates more resumption attempts by allowing a group of TLS servers to resume each other's TLS sessions. This modification provides the following savings for any TLS client that supports RFC 5077, including Windows Phone and Windows RT devices:

- Reduced resource usage on the server
- Reduced bandwidth, which improves the efficiency of client connections
- Reduced time spent for the TLS handshake due to resumptions of the connection

For information about stateless TLS session resumption, see the IETF document [RFC 5077](https://datatracker.ietf.org/doc/rfc5077/).

## Application protocol negotiation

Windows Server 2012 R2 and Windows 8.1 introduced support that allows client-side TLS application protocol negotiation. Applications can leverage protocols as part of the HTTP 2.0 standard development, and users can access online services such as Google and Twitter by using apps running the SPDY protocol.

For information about how application protocol negotiation works, see [Transport Layer Security (TLS) Application Layer Protocol Negotiation Extension](https://datatracker.ietf.org/doc/html/rfc7301).

## TLS support for Server Name Indication extensions

The Server Name Indication (SNI) feature extends the SSL and TLS protocols to allow proper identification of the server when numerous virtual images are running on a single server. In a virtual hosting scenario, several domains (each with its own potentially distinct certificate) are hosted on one server. In this case, the server has no way of knowing beforehand which certificate to send to the client. SNI allows the client to inform the target domain earlier in the protocol, and this allows the server to correctly select the proper certificate.

This provides the following additional functionality:

- Allows you to host multiple SSL websites on a single Internet Protocol and port combination
- Reduces the memory usage when multiple SSL websites are hosted on a single web server
- Allows more users to connect to SSL websites simultaneously