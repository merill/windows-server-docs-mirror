---
layout: Conceptual
title: Service Communications Certificates | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/service-communications-certificates
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: Learn more about service communications certificates in AD FS
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: best-practice
locale: en-us
document_id: 6dcb1637-27f2-41b4-5a55-cee8058479fd
document_version_independent_id: 1c9b7b0d-cf21-b5aa-54db-bdd4c5969f0e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Service-Communications-Certificates.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/service-communications-certificates
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Service-Communications-Certificates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: fbf3e955-7df4-e90b-a4be-23512c1fc40f
---

# Service Communications Certificates | Microsoft Learn

A federation server requires the use of service communication certificates for scenarios in which WCF message security is used.

## Service communication certificate requirements

Service communication certificates must meet the following requirements to work with AD FS:

- The service communication certificate must include the server authentication enhanced key usage (EKU) extension.
- The certificate revocation lists (CRLs) must be accessible for all the certificates in the chain from the service communication certificate to the root CA certificate. Any federation server proxies and Web servers that trust this federation server must also trust the root CA.
- The subject name that's used in the service communication certificate must match the Federation Service name in the properties of the Federation Service.

## Deployment considerations for service communication certificates

Configure service communication certificates so that all federation servers use the same certificate. If you're deploying the Federated Web Single-Sign-On (SSO) design, we recommend that a public CA issue your service communication certificate. You can request and install these certificates through the IIS Manager snap-in.

You can use self-signed, service communication certificates successfully on federation servers in a test lab environment. However, for a production environment, we recommend that you obtain service communication certificates from a public CA.

Reasons why you shouldn't use self-signed, service communication certificates for a live deployment include:

- A self-signed, SSL certificate must be added to the trusted root store on each of the federation servers in the resource partner organization. While a self-signed certificate alone doesn't enable an attacker to compromise a resource federation server, trusting self-signed certificates does increase the attack surface of a computer. If the certificate signer isn't trustworthy, it can lead to security vulnerabilities.
- A self-signed, service communication certificate creates a bad user experience. Clients receive Security Alert prompts when they try to access federated resources that display the following message: "The security certificate was issued by a company you have not chosen to trust." This message is expected, because the self-signed certificate isn't trusted.

    Note

    If necessary, you can work around this condition by using Group Policy to manually push down the self-signed certificate to the trusted root store on each client computer that attempts to access an AD FS site.
- CAs provide more certificate-based features, such as private key archive, renewal, and revocation that aren't provided by self-signed certificates.