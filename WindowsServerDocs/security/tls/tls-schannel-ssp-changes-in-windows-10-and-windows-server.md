---
layout: Conceptual
title: TLS (Schannel SSP) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/tls/tls-schannel-ssp-changes-in-windows-10-and-windows-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
ms.author: roharwoo
author: Andrei-Popov
description: 'Learn more about: TLS (Schannel SSP) changes in Windows 10 and Windows Server 2016'
ms.topic: how-to
ms.date: 2018-05-16T00:00:00.0000000Z
locale: en-us
document_id: 2b0c9c29-dda2-c057-e86e-4f4f138f8b3a
document_version_independent_id: 922203c0-ae2c-6f51-15da-1958455563de
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/tls/tls-schannel-ssp-changes-in-windows-10-and-windows-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/tls/tls-schannel-ssp-changes-in-windows-10-and-windows-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/tls/tls-schannel-ssp-changes-in-windows-10-and-windows-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: bfaf3cee-a714-d352-a183-55a7c5f004f5
---

# TLS (Schannel SSP) | Microsoft Learn

## Cipher Suite Changes

Windows 10, version 1511 and Windows Server 2016 add support for configuration of cipher suite order using Mobile Device Management (MDM).

For cipher suite priority order changes, see [Cipher Suites in Schannel](/en-us/windows/win32/secauthn/cipher-suites-in-schannel).

Added support for the following cipher suites:

- TLS\_ECDHE\_RSA\_WITH\_AES\_128\_GCM\_SHA256 (RFC 5289) in Windows 10, version 1507 and Windows Server 2016
- TLS\_ECDHE\_RSA\_WITH\_AES\_256\_GCM\_SHA384 (RFC 5289) in Windows 10, version 1507 and Windows Server 2016

DisabledByDefault change for the following cipher suites:

- TLS\_DHE\_DSS\_WITH\_AES\_256\_CBC\_SHA256 (RFC 5246) in Windows 10, version 1703
- TLS\_DHE\_DSS\_WITH\_AES\_128\_CBC\_SHA256 (RFC 5246) in Windows 10, version 1703
- TLS\_DHE\_DSS\_WITH\_AES\_256\_CBC\_SHA (RFC 5246) in Windows 10, version 1703
- TLS\_DHE\_DSS\_WITH\_AES\_128\_CBC\_SHA (RFC 5246) in Windows 10, version 1703
- TLS\_DHE\_DSS\_WITH\_3DES\_EDE\_CBC\_SHA (RFC 5246) in Windows 10, version 1703
- TLS\_RSA\_WITH\_RC4\_128\_SHA in Windows 10, version 1709
- TLS\_RSA\_WITH\_RC4\_128\_MD5 in Windows 10, version 1709

Starting with Windows 10, version 1507 and Windows Server 2016, SHA 512 certificates are supported by default.

### RSA key changes

Windows 10, version 1507 and Windows Server 2016 add registry configuration options for client RSA key sizes.

For more information, see [KeyExchangeAlgorithm key sizes](tls-registry-settings#keyexchangealgorithm-key-sizes).

### Diffie-Hellman key changes

Windows 10, version 1507 and Windows Server 2016 add registry configuration options for Diffie-Hellman key sizes.

For more information, see [KeyExchangeAlgorithm key sizes](tls-registry-settings#keyexchangealgorithm-key-sizes).

### SCH\_USE\_STRONG\_CRYPTO option changes

With Windows 10, version 1507 and Windows Server 2016, [SCH_USE_STRONG_CRYPTO](/en-us/windows/win32/api/schannel/ns-schannel-schannel_cred) option now disables NULL, MD5, DES, and export ciphers.

## Elliptical Curve changes

Windows 10, version 1507 and Windows Server 2016 add Group Policy configuration for elliptical curves under Computer Configuration &gt; Administrative Templates &gt; Network &gt; SSL Configuration Settings. The ECC Curve Order list specifies the order in which elliptical curves are preferred as well as enables supported curves which are not enabled.

Added support for the following elliptical curves:

- BrainpoolP256r1 (RFC 7027) in Windows 10, version 1507 and Windows Server 2016
- BrainpoolP384r1 (RFC 7027) in Windows 10, version 1507 and Windows Server 2016
- BrainpoolP512r1 (RFC 7027) in Windows 10, version 1507 and Windows Server 2016
- Curve25519 (RFC draft-ietf-tls-curve25519) in Windows 10, version 1607 and Windows Server 2016

## Dispatch level support for SealMessage & UnsealMessage

Windows 10, version 1507 and Windows Server 2016 add support for SealMessage/UnsealMessage at dispatch level.

## DTLS 1.2

Windows 10, version 1607 and Windows Server 2016 add support for DTLS 1.2 (RFC 6347).

## HTTP.SYS thread pool

Windows 10, version 1607 and Windows Server 2016 add registry configuration of the size of the thread pool used to handle TLS handshakes for HTTP.SYS.

Registry path:

HKLM\SYSTEM\CurrentControlSet\Control\LSA

To specify a maximum thread pool size per CPU core, create a **MaxAsyncWorkerThreadsPerCpu** entry. This entry does not exist in the registry by default. After you have created the entry, change the DWORD value to the desired size. If not configured, then the maximum is 2 threads per CPU core.

## Next Protocol Negotiation (NPN) support

Beginning with Windows 10 version 1703, Next Protocol Negotiation (NPN) has been removed and is no longer supported.

## Pre-Shared Key (PSK)

Windows 10, version 1607 and Windows Server 2016 add support for PSK key exchange algorithm (RFC 4279).

Added support for the following PSK cipher suites:

- TLS\_PSK\_WITH\_AES\_128\_CBC\_SHA256 (RFC 5487) in Windows 10, version 1607 and Windows Server 2016
- TLS\_PSK\_WITH\_AES\_256\_CBC\_SHA384(RFC 5487) in Windows 10, version 1607 and Windows Server 2016
- TLS\_PSK\_WITH\_NULL\_SHA256 (RFC 5487) in Windows 10, version 1607 and Windows Server 2016
- TLS\_PSK\_WITH\_NULL\_SHA384 (RFC 5487) in Windows 10, version 1607 and Windows Server 2016
- TLS\_PSK\_WITH\_AES\_128\_GCM\_SHA256 (RFC 5487) in Windows 10, version 1607 and Windows Server 2016
- TLS\_PSK\_WITH\_AES\_256\_GCM\_SHA384 (RFC 5487) in Windows 10, version 1607 and Windows Server 2016

## Session Resumption without Server-Side State server-side performance improvements

Windows 10, version 1507 and Windows Server 2016 provide 30% more session resumptions per second with session tickets compared to Windows Server 2012.

## Session Hash and Extended Master Secret Extension

Windows 10, version 1507 and Windows Server 2016 add support for RFC 7627: Transport Layer Security (TLS) Session Hash and Extended Master Secret Extension.

Due to this change, Windows 10 and Windows Server 2016 requires 3rd party [CNG SSL provider](/en-us/windows/win32/seccng/cng-ssl-provider-functions) updates to support NCRYPT\_SSL\_INTERFACE\_VERSION\_3, and to describe this new interface.

## SSL support

Beginning with Windows 10, version 1607 and Windows Server 2016, the TLS client and server SSL 3.0 is disabled by default. This means that unless the application or service specifically requests SSL 3.0 via the SSPI, the client will never offer or accept SSL 3.0 and the server will never select SSL 3.0.

Beginning with Windows 10 version 1607 and Windows Server 2016, SSL 2.0 has been removed and is no longer supported.

## Changes to Windows TLS adherence to TLS 1.2 requirements for connections with non-compliant TLS clients

In TLS 1.2, the client uses the ["signature_algorithms" extension](https://tools.ietf.org/html/rfc5246#section-7.4.1.4.1) to indicate to the server which signature/hash algorithm pairs may be used in digital signatures (i.e., server certificates and server key exchange). The TLS 1.2 RFC also requires that the server Certificate message honor "signature\_algorithms" extension:

"If the client provided a "signature\_algorithms" extension, then all certificates provided by the server MUST be signed by a hash/signature algorithm pair that appears in that extension."

In practice, some third-party TLS clients do not comply with the TLS 1.2 RFC and fail to include all the signature and hash algorithm pairs they are willing to accept in the "signature\_algorithms" extension, or omit the extension altogether (the latter indicates to the server that the client only supports SHA1 with RSA, DSA or ECDSA).

A TLS server often only has one certificate configured per endpoint, which means the server can't always supply a certificate that meets the client's requirements.

Prior to Windows 10 and Windows Server 2016, the Windows TLS stack strictly adhered to the TLS 1.2 RFC requirements, resulting in connection failures with RFC non-compliant TLS clients and interoperability issues. In Windows 10 and Windows Server 2016, the constraints are relaxed and the server can send a certificate that does not comply with TLS 1.2 RFC, if that's the server's only option. The client may then continue or terminate the handshake.

When validating server and client certificates, the Windows TLS stack strictly complies with the TLS 1.2 RFC and only allows the negotiated signature and hash algorithms in the server and client certificates.