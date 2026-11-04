---
layout: Conceptual
title: Kerberos Constrained Delegation Overview in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/kerberos/kerberos-constrained-delegation-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about the new capabilities for Kerberos constrained delegation in Windows Server.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-25T00:00:00.0000000Z
locale: en-us
document_id: 1b8ae5c0-92f8-31b5-18e1-c62dacb1aec1
document_version_independent_id: dea7c908-2bbd-91c2-9bde-db81bbb94ab1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/kerberos/kerberos-constrained-delegation-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/kerberos/kerberos-constrained-delegation-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/kerberos/kerberos-constrained-delegation-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 02c15786-eaa3-2316-381e-c7229bbd6fae
---

# Kerberos Constrained Delegation Overview in Windows Server | Microsoft Learn

This article describes new capabilities for Kerberos constrained delegation in Windows Server.

## Feature description

Kerberos constrained delegation was introduced in Windows Server to provide a safer form of delegation that could be used by services. When it's configured, constrained delegation restricts the services to which the specified server can act on the behalf of a user. This requires domain admin privileges to configure a domain account for a service and restricts the account to a single domain. In modern enterprises, front-end services aren't designed to integrate only with services in their domain.

In earlier operating systems, domain admins configured the service, and service admins had no way to know which front-end services delegated to the resource services they owned. And any front-end service that could delegate to a resource service represented a potential attack point. If a server that hosted a front-end service was compromised, and it was configured to delegate to resource services, the resource services could also be compromised.

In Windows Server 2012 R2 and Windows Server 2012, the ability to configure constrained delegation for the service is transferred from the domain admin to the service admin. In this way, the back-end service administrator can allow or deny front-end services.

The Windows Server 2012 R2 and Windows Server 2012 implementation of the Kerberos protocol includes extensions specifically for constrained delegation. Service for User to Proxy (S4U2Proxy) allows a service to use its Kerberos service ticket for a user to obtain a service ticket from the Key Distribution Center (KDC) to a back-end service. These extensions allow constrained delegation to be configured on the back-end service's account, which can be in another domain. For more information about these extensions, see [\[MS-SFU\]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol Specification](/en-us/openspecs/windows_protocols/ms-sfu/3bff5864-8135-400e-bdd9-33b552051d94) in the MSDN Library.

## Practical applications

Constrained delegation lets service admins specify and enforce application trust boundaries by limiting where application services can act on a user's behalf. Service administrators can configure which front-end service accounts can delegate to their back-end services.

Front-end services like Microsoft Internet Security and Acceleration (ISA) Server, Microsoft Forefront Threat Management Gateway, Microsoft Exchange Outlook Web Access (OWA), and Microsoft SharePoint Server can use constrained delegation to authenticate to servers in other domains. This provides support for across domains service solutions by using an existing Kerberos infrastructure. Kerberos constrained delegation can be managed by domain administrators or service administrators.

## Resource-based constrained delegation across domains

Kerberos constrained delegation lets you provide constrained delegation when the front-end service and the resource services aren't in the same domain. Service administrators can configure the new delegation by specifying the domain accounts of the front-end services that can impersonate users on the account objects of the resource services.

### What value does this change add?

Services can use constrained delegation to authenticate to servers in other domains instead of using unconstrained delegation. This provides authentication support for cross-domain service solutions using an existing Kerberos infrastructure without requiring trust in front-end services to delegate to any service.

This also shifts the decision of whether a server should trust the source of a delegated identity from the delegating-from domain administrator to the resource owner.

### What works differently?

A change in the underlying protocol allows constrained delegation across domains. The Windows Server 2012 R2 and Windows Server 2012 implementation of the Kerberos protocol includes extensions to the Service for User to Proxy (S4U2Proxy) protocol. This is a set of extensions to the Kerberos protocol that allows a service to use its Kerberos service ticket for a user to obtain a service ticket from the Key Distribution Center (KDC) to a back-end service.

For implementation information about these extensions, see [\[MS-SFU\]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol Specification](/en-us/openspecs/windows_protocols/ms-sfu/3bff5864-8135-400e-bdd9-33b552051d94) in MSDN.

For more information about the basic message sequence for Kerberos delegation with a forwarded ticket-granting ticket (TGT) as compared to Service for User (S4U) extensions, see section [1.3.3 Protocol Overview](/en-us/openspecs/windows_protocols/ms-sfu/1fb9caca-449f-4183-8f7a-1a5fc7e7290a) in the [MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol Specification.

### Security Implications of Resource-based Constrained Delegation

Resource-based constrained delegation gives control of delegation to the administrator who owns the resource being accessed. It depends on attributes of the resource service rather than the service being trusted to delegate. As a result, resource-based constrained delegation can't use the Trusted-to-Authenticate-for-Delegation bit that previously controlled protocol transition. The KDC always allows protocol transition when performing resource-based constrained delegation as though the bit were set.

Because the KDC doesn't limit protocol transition, two new well-known SIDs give this control to the resource administrator. These SIDs identify whether protocol transition has occurred, and can be used with standard access control lists to grant or limit access as needed.

| SID | Description |
| --- | --- |
| AUTHENTICATION\_AUTHORITY\_ASSERTED\_IDENTITYS-1-18-1 | A SID that means the client's identity is asserted by an authentication authority based on proof of possession of client credentials. |
| SERVICE\_ASSERTED\_IDENTITYS-1-18-2 | A SID that means the client's identity is asserted by a service. |

A backend service can use standard ACL expressions to determine how the user was authenticated.

### How do you configure Resource-based Constrained Delegation?

To configure a resource service to let front-end services access resources on behalf of users, use Windows PowerShell cmdlets.

- To retrieve a list of principals, use the **Get-ADComputer**, **Get-ADServiceAccount**, and **Get-ADUser** cmdlets with the **Properties PrincipalsAllowedToDelegateToAccount** parameter.
- To configure the resource service, use the **New-ADComputer**, **New-ADServiceAccount**, **New-ADUser**, **Set-ADComputer**, **Set-ADServiceAccount**, and **Set-ADUser** cmdlets with the **PrincipalsAllowedToDelegateToAccount** parameter.