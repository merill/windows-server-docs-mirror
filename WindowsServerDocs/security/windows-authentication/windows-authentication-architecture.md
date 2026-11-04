---
layout: Conceptual
title: Windows Authentication Architecture | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/windows-authentication-architecture
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about the basic architectural scheme for Windows authentication.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2016-10-12T00:00:00.0000000Z
locale: en-us
document_id: 864a524b-ca6a-16f9-c2f2-2e388796b158
document_version_independent_id: 87f20915-fef9-50c9-d7b9-ae3c340c2d7a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/windows-authentication/windows-authentication-architecture.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/windows-authentication/windows-authentication-architecture
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/windows-authentication/windows-authentication-architecture.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 51c426d0-d817-b1fa-9b3e-132741edf551
---

# Windows Authentication Architecture | Microsoft Learn

This overview topic for the IT professional explains the basic architectural scheme for Windows authentication.

Authentication is the process by which the system validates a user's logon or sign-in information. A user's name and password are compared against an authorized list, and if the system detects a match, access is granted to the extent specified in the permission list for that user.

As part of an extensible architecture, the Windows Server operating systems implement a default set of authentication security support providers, which include Negotiate, the Kerberos protocol, NTLM, Schannel (secure channel), and Digest. The protocols used by these providers enable authentication of users, computers, and services, and the authentication process enables authorized users and services to access resources in a secure manner.

In Windows Server, applications authenticate users by using the SSPI to abstract calls for authentication. Thus, developers do not need to understand the complexities of specific authentication protocols or build authentication protocols into their applications.

Windows Server operating systems include a set of security components that make up the Windows security model. These components ensure that applications cannot gain access to resources without authentication and authorization. The following sections describe the elements of the authentication architecture.

### Local Security Authority

The Local Security Authority (LSA) is a protected subsystem that authenticates and signs in users to the local computer. In addition, LSA maintains information about all aspects of local security on a computer (these aspects are collectively known as the local security policy). It also provides various services for translation between names and security identifiers (SIDs).

The security subsystem keeps track of the security policies and the accounts that are on a computer system. In the case of a domain controller, these policies and accounts are those that are in effect for the domain in which the domain controller is located. These policies and accounts are stored in Active Directory. The LSA subsystem provides services for validating access to objects, checking user rights, and generating audit messages.

### Security Support Provider Interface

The Security Support Provider Interface (SSPI) is the API that obtains integrated security services for authentication, message integrity, message privacy, and security quality-of-service for any distributed application protocol.

SSPI is the implementation of the Generic Security Service API (GSSAPI). SSPI provides a mechanism by which a distributed application can call one of several security providers to obtain an authenticated connection without knowledge of the details of the security protocol.

## Additional References

- [Security Support Provider Interface Architecture](security-support-provider-interface-architecture)
- [Credentials Processes in Windows Authentication](credentials-processes-in-windows-authentication)
- [Windows Authentication Technical Overview](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dn169029%28v=ws.10%29)