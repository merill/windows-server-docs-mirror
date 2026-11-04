---
layout: Conceptual
title: Kerberos authentication overview in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/kerberos/kerberos-authentication-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Explore Kerberos authentication in Windows Server, including its protocol, benefits, interoperability, and practical applications.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2026-09-14T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 6a5145ff-059a-67db-0c24-34f8b63fda6a
document_version_independent_id: af9468c7-e7f1-a22a-4b99-1acad8c8de62
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/kerberos/kerberos-authentication-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/kerberos/kerberos-authentication-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/kerberos/kerberos-authentication-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a1b3283e-1d0f-4505-097e-91111127bc2e
---

# Kerberos authentication overview in Windows Server | Microsoft Learn

Kerberos is an authentication protocol that is used to verify the identity of a user or host. This topic contains information about Kerberos authentication in Windows Server and Windows.

The Windows Server operating systems implement the Kerberos version 5 authentication protocol and extensions for public key authentication, transporting authorization data, and delegation. The Kerberos authentication client is implemented as a security support provider (SSP), and it can be accessed through the Security Support Provider Interface (SSPI). Initial user authentication is integrated with the Winlogon single sign-on architecture.

The Kerberos Key Distribution Center (KDC) is integrated with other Windows Server security services that run on the domain controller. The KDC uses the domain's Active Directory Domain Services database as its security account database. Active Directory Domain Services is required for default Kerberos implementations within the domain or forest.

## How Kerberos authentication works

Kerberos authentication involves three parties: the client that acts for a security principal, the service the principal wants to reach, and the Key Distribution Center (KDC) that both parties trust. A *security principal* is an identity, such as a user, computer, or service, that the system can authenticate. In Windows Server, the KDC runs on every domain controller and uses the domain's Active Directory Domain Services database as its account database.

When a user signs in, the Kerberos client contacts the KDC to prove the user's identity and obtain a ticket-granting ticket (TGT). The TGT is a credential that lets the client request access to services without presenting the user's password again. The client stores the TGT in its ticket cache and reuses it until the ticket expires.

To connect to a service, the client presents its TGT to the KDC and requests a service ticket for that specific service. The KDC returns a service ticket, which the client presents directly to the target service. Because the ticket already contains the information that the service needs to verify the client's identity, the service can authenticate the client without contacting a domain controller for each connection.

Windows Server implements the industry-standard Kerberos version 5 protocol that the Internet Engineering Task Force (IETF) defines. This standards-track foundation lets the Windows implementation interoperate with other systems that use Kerberos. On top of the standard, Windows adds extensions for public key authentication, transporting authorization data, and delegation. Microsoft documents these Windows-specific behaviors in the Windows Protocols specification [\[MS-KILE\]: Kerberos Protocol Extensions](/en-us/openspecs/windows_protocols/ms-kile/2a32282e-dd48-4ad9-a542-609804b02cc9), which describes where the Windows implementation extends or differs from the standard.

## Practical applications

The benefits gained by using Kerberos for domain-based authentication are described in the following sections.

### Delegated authentication

Services that run on Windows operating systems can impersonate a client computer when accessing resources on the client's behalf. In many cases, a service can complete its work for the client by accessing resources on the local computer. When a client computer authenticates to the service, NTLM and Kerberos protocol provide the authorization information that a service needs to impersonate the client computer locally. However, some distributed applications are designed so that a front-end service must use the client computer's identity when it connects to back-end services on other computers. Kerberos authentication supports a delegation mechanism that enables a service to act on behalf of its client when connecting to other services.

### Single sign on

Using Kerberos authentication within a domain or in a forest allows the user or service access to resources permitted by administrators without multiple requests for credentials. After initial domain sign on through Winlogon, Kerberos manages the credentials throughout the forest whenever access to resources is attempted.

### Interoperability

The implementation of the Kerberos V5 protocol by Microsoft is based on standards-track specifications that are recommended to the Internet Engineering Task Force (IETF). As a result, in Windows operating systems, the Kerberos protocol lays a foundation for interoperability with other networks in which the Kerberos protocol is used for authentication. In addition, Microsoft publishes Windows Protocols documentation for implementing the Kerberos protocol. The documentation contains the technical requirements, limitations, dependencies, and Windows-specific protocol behavior for Microsoft's implementation of the Kerberos protocol.

### More efficient authentication to servers

Before Kerberos, NTLM authentication could be used, which requires an application server to connect to a domain controller to authenticate every client computer or service. With the Kerberos protocol, renewable session tickets replace pass-through authentication. The server is not required to go to a domain controller, unless it needs to validate a Privilege Attribute Certificate (PAC). Instead, the server can authenticate the client computer by examining credentials presented by the client. Client computers can obtain credentials for a particular server once and then reuse those credentials throughout a network logon session.

### Mutual authentication

By using the Kerberos protocol, a party at either end of a network connection can verify that the party on the other end is the entity it claims to be. NTLM does not enable clients to verify a server's identity or enable one server to verify the identity of another. NTLM authentication was designed for a network environment in which servers were assumed to be genuine. The Kerberos protocol makes no such assumption.

## Encryption types

Beginning with Windows Server 2025, Kerberos no longer honors the legacy registry key `REG_DWORD SupportedEncryptionTypes` found in the path **HKEY\_LOCAL\_MACHINE\CurrentControlSet\Control\Lsa\Kerberos\Parameters**. Microsoft recommends using group policy instead. To learn more about the group policy settings, see [Network security: Configure encryption types allowed for Kerberos](/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/security-policy-settings/network-security-configure-encryption-types-allowed-for-kerberos).