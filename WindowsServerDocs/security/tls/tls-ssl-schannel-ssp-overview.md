---
layout: Conceptual
title: TLS/SSL overview (Schannel SSP) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/tls/tls-ssl-schannel-ssp-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
ms.author: roharwoo
author: Andrei-Popov
description: Learn about the TLS and SSL implementations in Windows using the Schannel Security Service Provider (SSP).
ms.topic: concept-article
ms.date: 2024-01-18T00:00:00.0000000Z
ms.custom: os_security, network_security
locale: en-us
document_id: 1d708a03-0fd7-71a9-3f9e-be86f30232b9
document_version_independent_id: 19ea4227-5d4a-6d8f-3800-389dea56b1a5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/tls/tls-ssl-schannel-ssp-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/tls/tls-ssl-schannel-ssp-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/tls/tls-ssl-schannel-ssp-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 9d96404d-922e-b88c-1b85-ac0cedc057c9
---

# TLS/SSL overview (Schannel SSP) | Microsoft Learn

This article is to introduce IT professionals to TLS and SSL implementations in Windows using the Schannel Security Service Provider (SSP) by describing practical applications, changes in Microsoft's implementation, software requirements, and other resources for Windows Server and client devices.

## Description

Schannel is a Security Support Provider (SSP) that implements the Secure Sockets Layer (SSL) and Transport Layer Security (TLS) Internet standard authentication protocols.

The Security Support Provider Interface (SSPI) is an API used by Windows systems to perform security-related functions including authentication. The SSPI functions as a common interface to several SSPs, including the Schannel SSP.

The Schannel authentication protocol suite provides several protocols that all use a client/server model. The following protocols are based on public key cryptography:

- TLS versions 1.0, 1.1, 1.2, and 1.3
- SSL versions 2.0 and 3.0
- Datagram Transport Layer Security (DTLS) versions 1.0 and 1.2
- Private Communications Transport (PCT)

Note

TLS 1.0 and TLS 1.1 is being deprecated in Windows starting with Windows 11 September Insider Preview build and later releases. To learn more, see [TLS 1.0 and TLS 1.1 deprecation in Windows](/en-us/windows/win32/secauthn/tls-10-11-deprecation-in-windows).

## Applications

One problem when you administer a network is securing data that is being sent between applications across an untrusted network. You can use TLS and SSL to authenticate servers and client computers and then use the protocol to encrypt messages between the authenticated parties.

For example, you can use TLS/SSL for:

- SSL-secured transactions with an e-commerce website
- Authenticated client access to an SSL-secured website
- Remote access
- SQL access
- E-mail

## Requirements

TLS and SSL protocols use a client/server model and are based on certificate authentication, which requires a public key infrastructure.

## Server Manager information

There are no configuration steps necessary to implement TLS, SSL or Schannel.