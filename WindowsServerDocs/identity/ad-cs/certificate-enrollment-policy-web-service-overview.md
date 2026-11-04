---
layout: Conceptual
title: Certificate Enrollment Policy Web Service overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/certificate-enrollment-policy-web-service-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn more about Certificate Enrollment Policy Web Service, including Server Manager configuration and authentication options.
author: robinharwood
ms.topic: concept-article
ms.author: roharwoo
ms.date: 2025-02-14T00:00:00.0000000Z
locale: en-us
document_id: 729d9c0d-7160-8cea-eb1f-7f89cd580b28
document_version_independent_id: 729d9c0d-7160-8cea-eb1f-7f89cd580b28
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/certificate-enrollment-policy-web-service-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/certificate-enrollment-policy-web-service-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/certificate-enrollment-policy-web-service-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 8211ef00-829a-f03f-c45e-06efe98a7ec4
---

# Certificate Enrollment Policy Web Service overview | Microsoft Learn

The Certificate Enrollment Policy Web Service lets users and computers obtain certificate enrollment policy information even when the computer isn't a member of a domain, or if the computer is domain-joined but temporarily outside of the secure corporate network. The Certificate Enrollment Policy Web Service works with the Certificate Enrollment Web Service to provide policy-based automatic certificate enrollment for these users and computers. The Certificate Enrollment Policy Web Service uses an enrollment protocol based on WS-Trust Jump. WS-Trust Jump enables certificate policy retrieval, certificate enrollment, and certificate renewal using hypertext transfer protocol (HTTP) over a secure sockets layer or transport layer security (SSL/TLS) encryption (HTTPS).

The Certificate Enrollment Policy Web Service communicates with Active Directory Domain Services (AD DS) using standard Lightweight Directory Access Protocol (LDAP) and the secure LDAP (LDAPS) ports, TCP 389, and TCP 636. The Certificate Enrollment Policy Web Service uses the credentials of the Internet Information Services (IIS) DefaultAppPool (ApplicationPoolIdentity) by default. You can't configure the account during role installation, but you can modify it using IIS manager after installation.

This article describes types of authentication you can use when configuring the Certificate Enrollment Policy Web Service in Server Manager. This article also describes the authentication options that Server Manager presents you when you use it to install the Certificate Enrollment Policy Web Service.

## Authentication types

Clients that communicate with the Certificate Enrollment Policy Web Service must use one of the following authentication types:

- Windows integrated authentication
- Client certificate authentication
- Username and password authentication

Note

If you want to configure key-based renewal, you must enable username and password authentication or client certificate authentication. The Certificate Enrollment Policy Web Service doesn't support anonymous authentication.

## Key-based renewal

Key-based renewal mode allows an existing valid certificate to be used to authenticate a certificate renewal request. This feature allows computers that aren't connected directly to the internal network to automatically renew an existing certificate.

Note

When you enable key-based renewal mode for the Certificate Enrollment Policy Web Service, the service doesn't accept requests for new certificates. You can install multiple instances of the Certificate Enrollment Policy Web Service on Windows Server, but you must use the [Install-AdcsEnrollmentPolicyWebService](/en-us/powershell/module/adcsdeployment/install-adcsenrollmentpolicywebservice) PowerShell cmdlet to install and configure new instances.

## Server certificate

The Certificate Enrollment Web Service and the Certificate Enrollment Policy Web Service must use Secure Sockets Layer (SSL) for communication with clients, which they can accomplish by using HTTPS. Each service must have a valid certificate with an enhanced key usage (EKU) policy of Server Authentication in the local computer certificate store.

Note

If you haven't provided an SSL certificate to the server hosting the Certificate Enrollment Web Service yet, follow the instructions in [Configure SSL/TLS on a Web site in the domain with an Enterprise CA](https://social.technet.microsoft.com/wiki/contents/articles/12485.configure-ssltls-on-a-web-site-in-the-domain-with-an-enterprise-ca.aspx).