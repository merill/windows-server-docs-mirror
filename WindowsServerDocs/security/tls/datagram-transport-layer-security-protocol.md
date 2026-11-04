---
layout: Conceptual
title: Datagram Transport Layer Security protocol | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/tls/datagram-transport-layer-security-protocol
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
ms.author: roharwoo
author: Andrei-Popov
description: Learn about the Datagram Transport Layer Security protocol, which is part of the Schannel Security Support Provider.
ms.topic: concept-article
ms.date: 2018-05-16T00:00:00.0000000Z
locale: en-us
document_id: 7f73895e-b371-4345-3fe8-882da9b47256
document_version_independent_id: c14eb3b9-3f59-6546-151d-44d1ed264025
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/tls/datagram-transport-layer-security-protocol.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/tls/datagram-transport-layer-security-protocol
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/tls/datagram-transport-layer-security-protocol.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 099436a2-1e44-49b1-33c7-d09398b84853
---

# Datagram Transport Layer Security protocol | Microsoft Learn

Windows Server 2016, Windows 10

This reference topic for the IT professional describes the Datagram Transport Layer Security (DTLS) protocol, which is part of the Schannel Security Support Provider (SSP).

Introduced in the Schannel SSP in Windows Server 2012 and Windows 8, the DTLS protocol provides communication privacy for datagram protocols. For information about which DTLS version is supported in Windows versions, see [Protocols in TLS/SSL (Schannel SSP)](/en-us/windows/win32/secauthn/protocols-in-tls-ssl--schannel-ssp-). The protocol allows client and server applications to communicate in a way that is designed to prevent eavesdropping, tampering, or message forgery. The DTLS protocol is based on the Transport Layer Security (TLS) protocol, and it provides equivalent security guarantees, reducing the need to use IPsec or designing a custom application layer security protocol.

Datagrams are common in streaming media, such as gaming or secured video conferencing. Developers can develop applications to use the DTLS protocol within the context of the Windows authentication Security Support Provider Interface (SSPI) model to secure the communication between clients and servers. The DTLS protocol is built on top of the User Datagram Protocol (UDP). DTLS is designed to be as similar to TLS as possible to minimize new security invention and to maximize the amount of code and infrastructure reuse.

The cipher suites that are available for configuration are patterned after those you can configure for TLS. RC4 is not permitted. Schannel continues to use Cryptography Next Generation (CNG). This takes advantage of FIPS 140 certification, which was introduced in Windows Vista.

## Additional References

[IETF RFC 4347 Datagram Transport Layer Security](https://datatracker.ietf.org/doc/html/rfc4347)