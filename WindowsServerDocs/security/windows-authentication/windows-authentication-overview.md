---
layout: Conceptual
title: Windows Authentication Overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/windows-authentication-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about lists documentation resources for Windows authentication and logon technologies that include product evaluation, getting started guides, procedures, design and deployment guides, technical references, and command references.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-29T00:00:00.0000000Z
locale: en-us
document_id: bd2e1750-187e-6174-65c0-5fc82db5f9ab
document_version_independent_id: 36927386-f1d8-822b-d449-a8a97296b083
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/windows-authentication/windows-authentication-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/windows-authentication/windows-authentication-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/windows-authentication/windows-authentication-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 94bb7f57-0e7e-09d2-7faa-7a527256e0fb
---

# Windows Authentication Overview | Microsoft Learn

This navigation topic for the IT professional lists documentation resources for Windows authentication and logon technologies that include product evaluation, getting started guides, procedures, design and deployment guides, technical references, and command references.

## Feature description

Authentication is a process for verifying the identity of an object, service or person. When you authenticate an object, the goal is to verify that the object is genuine. When you authenticate a service or person, the goal is to verify that the credentials presented are authentic.

In a networking context, authentication is the act of proving identity to a network application or resource. Typically, identity is proven by a cryptographic operation that uses either a key only the user knows - as with public key cryptography - or a shared key. The server side of the authentication exchange compares the signed data with a known cryptographic key to validate the authentication attempt.

Storing the cryptographic keys in a secure central location makes the authentication process scalable and maintainable. Active Directory Domain Services is the recommended and default technology for storing identity information (including the cryptographic keys that are the user's credentials). Active Directory is required for default NTLM and Kerberos implementations.

Authentication techniques range from a simple logon, which identifies users based on something that only the user knows - like a password, to more powerful security mechanisms that use something that the user has - like tokens, public key certificates, and biometrics. In a business environment, services or users might access multiple applications or resources on many types of servers within a single location or across multiple locations. For these reasons, authentication must support environments for other platforms and for other Windows operating systems.

The Windows operating system implements a default set of authentication protocols, including Kerberos, NTLM, Transport Layer Security/Secure Sockets Layer (TLS/SSL), and Digest, as part of an extensible architecture. In addition, some protocols are combined into authentication packages such as Negotiate and the Credential Security Support Provider. These protocols and packages enable authentication of users, computers, and services; the authentication process, in turn, enables authorized users and services to access resources in a secure manner.

For more information about Windows Authentication including

- [Windows Authentication Concepts](windows-authentication-concepts)
- [Windows Logon Scenarios](windows-logon-scenarios)
- [Windows Authentication Architecture](windows-authentication-architecture)
- [Security Support Provider Interface Architecture](security-support-provider-interface-architecture)
- [Credentials Processes in Windows Authentication](credentials-processes-in-windows-authentication)
- [Group Policy Settings Used in Windows Authentication](group-policy-settings-used-in-windows-authentication)

See the [Windows Authentication Technical Overview](windows-authentication-technical-overview).

## Practical applications

Windows Authentication is used to verify that the information comes from a trusted source, whether from a person or computer object, such as another computer. Windows provides many different methods to achieve this goal as described below.

| To... | Feature | Description |
| --- | --- | --- |
| Authenticate within an Active Directory domain | Kerberos | The Microsoft Windows Server operating systems implement the Kerberos version 5 authentication protocol and extensions for public key authentication. The Kerberos authentication client is implemented as a security support provider (SSP) and can be accessed through the Security Support Provider Interface (SSPI). Initial user authentication is integrated with the Winlogon single sign-on architecture. The Kerberos Key Distribution Center (KDC) is integrated with other Windows Server security services running on the domain controller. The KDC uses the domain's Active Directory directory service database as its security account database. Active Directory is required for default Kerberos implementations.<br>For additional resources, see [Kerberos Authentication Overview](../kerberos/kerberos-authentication-overview). |
| Secure authentication on the web | TLS/SSL as implemented in the Schannel Security Support Provider | The Transport Layer Security (TLS) protocol versions 1.0, 1.1, and 1.2, Secure Sockets Layer (SSL) protocol, versions 2.0 and 3.0, Datagram Transport Layer Security protocol version 1.0, and the Private Communications Transport (PCT) protocol, version 1.0, are based on public key cryptography. The Secure Channel (Schannel) provider authentication protocol suite provides these protocols. All Schannel protocols use a client and server model.<br>For additional resources, see [TLS - SSL (Schannel SSP) Overview](../tls/tls-ssl-schannel-ssp-overview). |
| Authenticate to a web service or application | Integrated Windows Authentication | For additional resources, see [Integrated Windows Authentication](/en-us/aspnet/web-api/overview/security/integrated-windows-authentication). |
| Authenticate to legacy applications | NTLM | NTLM is a challenge-response style authentication protocol. In addition to authentication, the NTLM protocol optionally provides for session security--specifically message integrity and confidentiality through signing and sealing functions in NTLM.<br>For additional resources, see [NTLM Overview](../kerberos/ntlm-overview). |
| Leverage multifactor authentication | Smart card support<br>Biometric support | Smart cards are a tamper-resistant and portable way to provide security solutions for tasks such as client authentication, logging on to domains, code signing, and securing e-mail.<br>Biometrics relies on measuring an unchanging physical characteristic of a person to uniquely identify that person. Fingerprints are one of the most frequently used biometric characteristics, with millions of fingerprint biometric devices that are embedded in personal computers and peripherals.<br><br>For additional resources, see [Smart Card Technical Reference](/en-us/windows/security/identity-protection/smart-cards/smart-card-windows-smart-card-technical-reference). |
| Provide local management, storage and reuse of credentials | Credentials management<br>Local Security Authority<br><br>Passwords | Credential management in Windows ensures that credentials are stored securely. Credentials are collected on the Secure Desktop (for local or domain access), through apps or through websites so that the correct credentials are presented for every time a resource is accessed. |
| Extend modern authentication protection to legacy systems | Extended Protection for Authentication | This feature enhances the protection and handling of credentials when authenticating network connections by using Integrated Windows Authentication (IWA). |

## Software requirements

Windows Authentication is designed to be compatible with previous versions of the Windows operating system. However, improvements with each release aren't necessarily applicable to previous versions. Refer to documentation about specific features for more information.

## Server Manager information

Many authentication features can be configured using Group Policy, which can be installed using Server Manager. The Windows Biometric Framework feature is installed using Server Manager. Other server roles which are dependent upon authentication methods, such as Web Server (IIS) and Active Directory Domain Services, can also be installed using Server Manager.

## Related resources

| Authentication technologies | Resources |
| --- | --- |
| Windows authentication | [Windows Authentication Technical Overview](windows-authentication-technical-overview)Includes topics addressing differences between versions, general authentication concepts, logon scenarios, architectures for supported versions, and applicable settings. |
| Kerberos | [Kerberos Authentication Overview](../kerberos/kerberos-authentication-overview)<br>[Kerberos Constrained Delegation Overview](../kerberos/kerberos-constrained-delegation-overview)<br><br>[Kerberos forum](/en-us/answers/topics/windows-server-security.html) |
| TLS/SSL and DTLS (Schannel security support provider) | [TLS - SSL (Schannel SSP) Overview](../tls/tls-ssl-schannel-ssp-overview)<br>[Schannel Security Support Provider Technical Reference](../tls/schannel-security-support-provider-technical-reference) |
| NTLM | [NTLM Overview](../kerberos/ntlm-overview)Contains links to current and past resources |
| PKU2U | [Introducing PKU2U in Windows](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd560634%28v=ws.10%29) |
| Smart Card | [Smart Card Technical Reference](/en-us/windows/security/identity-protection/smart-cards/smart-card-windows-smart-card-technical-reference) |
| Credentials | [Credentials Protection and Management](../credentials-protection-and-management/credentials-protection-and-management)Contains links to current and past resources<br>[Passwords Overview](../kerberos/passwords-overview)Contains links to current and past resources |