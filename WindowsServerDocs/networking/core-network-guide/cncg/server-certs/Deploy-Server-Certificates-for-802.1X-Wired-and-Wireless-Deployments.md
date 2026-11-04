---
layout: Conceptual
title: Deploy Server Certificates for 802.1X Wired and Wireless Deployments | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/server-certs/deploy-server-certificates-for-802.1x-wired-and-wireless-deployments
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to deploy server certificates to your Remote Access and Network Policy Server (NPS) infrastructure servers.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: d5cb89fa-6274-b6ae-551c-538c546ad448
document_version_independent_id: d50eaab3-0f04-1cf1-11b6-a9896b42331f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Deploy-Server-Certificates-for-802.1X-Wired-and-Wireless-Deployments.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/server-certs/deploy-server-certificates-for-802.1x-wired-and-wireless-deployments
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Deploy-Server-Certificates-for-802.1X-Wired-and-Wireless-Deployments.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 082ccd29-98b2-1608-f5f6-ff9f4311e58b
---

# Deploy Server Certificates for 802.1X Wired and Wireless Deployments | Microsoft Learn

You can use this guide to deploy server certificates to your Remote Access and Network Policy Server (NPS) infrastructure servers.

This guide contains the following sections.

- Prerequisites for using this guide
- What this guide does not provide
- Technology overviews
- [Server Certificate Deployment Overview](server-certificate-deployment-overview)
- [Server Certificate Deployment Planning](server-certificate-deployment-planning)
- [Server Certificate Deployment](server-certificate-deployment)

### **Digital server certificates**

This guide provides instructions for using Active Directory Certificate Services (AD CS) to automatically enroll certificates to Remote Access and NPS infrastructure servers. AD CS allows you to build a public key infrastructure (PKI) and provide public key cryptography, digital certificates, and digital signature capabilities for your organization.

When you use digital server certificates for authentication between computers on your network, the certificates provide:

1. Confidentiality through encryption.
2. Integrity through digital signatures.
3. Authentication by associating certificate keys with computer, user, or device accounts on a computer network.

### **Server types**

By using this guide, you can deploy server certificates to the following types of servers.

- Servers that are running the Remote Access service, that are DirectAccess or standard virtual private network (VPN) servers, and that are members of the **RAS and IAS Servers** group.
- Servers that are running the Network Policy Server (NPS) service that are members of the **RAS and IAS Servers** group.

### **Advantages of certificate autoenrollment**

Automatic enrollment of server certificates, also called autoenrollment, provides the following advantages.

- The AD CS certification authority (CA) automatically enrolls a server certificate to all of your NPS and Remote Access servers.
- All computers in the domain automatically receive your CA certificate, which is installed in the Trusted Root Certification Authorities store on every domain member computer. Because of this, all computers in the domain trust the certificates that are issued by your CA. This trust allows your authentication servers to prove their identities to each other and engage in secure communications.
- Other than refreshing Group Policy, the manual reconfiguration of every server is not required.
- Every server certificate includes both the Server Authentication purpose and the Client Authentication purpose in Enhanced Key Usage (EKU) extensions.
- Scalability. After deploying your Enterprise Root CA with this guide, you can expand your public key infrastructure (PKI) by adding Enterprise subordinate CAs.
- Manageability. You can manage AD CS by using the AD CS console or by using Windows PowerShell commands and scripts.
- Simplicity. You specify the servers that enroll server certificates by using Active Directory group accounts and group membership.
- When you deploy server certificates, the certificates are based on a template that you configure with the instructions in this guide. This means that you can customize different certificate templates for specific server types, or you can use the same template for all server certificates that you want to issue.

## Prerequisites for using this guide

This guide provides instructions on how to deploy server certificates by using AD CS and the Web Server (IIS) server role in Windows Server 2016. Following are the prerequisites for performing the procedures in this guide.

- You must deploy a core network using the Windows Server 2016 Core Network Guide, or you must already have the technologies provided in the Core Network Guide installed and functioning correctly on your network. These technologies include TCP/IP v4, DHCP, Active Directory Domain Services (AD DS), DNS, and NPS.

    Note

    The Windows Server 2016 Core Network Guide is available in the Windows Server 2016 Technical Library. For more information, see [Core Network Guide](../../core-network-guide).
- You must read the planning section of this guide to ensure that you are prepared for this deployment before you perform the deployment.
- You must perform the steps in this guide in the order in which they are presented. Do not jump ahead and deploy your CA without performing the steps that lead up to deploying the server, or your deployment will fail.
- You must be prepared to deploy two new servers on your network - one server upon which you will install AD CS as an Enterprise Root CA, and one server upon which you will install Web Server (IIS) so that your CA can publish the certificate revocation list (CRL) to the Web server.

Note

You are prepared to assign a static IP address to the Web and AD CS servers that you deploy with this guide, as well as to name the computers according to your organization naming conventions. In addition, you must join the computers to your domain.

## What this guide does not provide

This guide does not provide comprehensive instructions for designing and deploying a public key infrastructure (PKI) by using AD CS. It is recommended that you review AD CS documentation and PKI design documentation before deploying the technologies in this guide.

## Technology overviews

Following are technology overviews for AD CS and Web Server (IIS).

### Active Directory Certificate Services

AD CS in Windows Server 2016 provides customizable services for creating and managing the X.509 certificates that are used in software security systems that employ public key technologies. Organizations can use AD CS to enhance security by binding the identity of a person, device, or service to a corresponding public key. AD CS also includes features that allow you to manage certificate enrollment and revocation in a variety of scalable environments.

For more information, see [Active Directory Certificate Services Overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831740%28v=ws.11%29) and [Public Key Infrastructure Design Guidance](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-i-design-and-planning/ba-p/396953).

### Web Server (IIS)

The Web Server (IIS) role in Windows Server 2016 provides a secure, easy-to-manage, modular, and extensible platform for reliably hosting websites, services, and applications. With IIS, you can share information with users on the Internet, an intranet, or an extranet. IIS is a unified web platform that integrates IIS, ASP.NET, FTP services, PHP, and Windows Communication Foundation (WCF).

For more information, see [Web Server (IIS) Overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831725%28v=ws.11%29).