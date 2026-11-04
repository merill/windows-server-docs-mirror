---
layout: Conceptual
title: What is Active Directory Certificate Services in Windows Server? | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/active-directory-certificate-services-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about Active Directory Certificate Services (AD CS) in Windows Server and how it enhances security with certificates for authentication and encryption.
author: robinharwood
ms.author: roharwoo
ms.topic: overview
ms.date: 2026-05-12T00:00:00.0000000Z
locale: en-us
document_id: 38ac545e-2cc1-6b55-b7d4-21f6d24763c1
document_version_independent_id: 38ac545e-2cc1-6b55-b7d4-21f6d24763c1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/active-directory-certificate-services-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/active-directory-certificate-services-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/active-directory-certificate-services-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: a0fa0f98-510d-5d7b-a50f-97ddafb9d676
---

# What is Active Directory Certificate Services in Windows Server? | Microsoft Learn

Active Directory Certificate Services (AD CS) is a Windows Server role for issuing and managing public key infrastructure (PKI) certificates used in secure communication and authentication protocols.

## Issue and manage certificates

Digital certificates can be used to encrypt and digitally sign electronic documents and messages as well as for authentication of computer, user, or device accounts on a network. For example, digital certificates provide:

- Confidentiality through encryption.
- Integrity through digital signatures.
- Authentication by associating certificate keys with the computer, user, or device accounts on a computer network.

## Key features

AD CS provides the following important features:

- **Certification authorities:** Root and subordinate Certificate Authorities (CAs) are used to issue certificates to users, computers, and services, and to manage certificate validity.
- **Web enrollment:** Web enrollment allows users to connect to a CA with a Web browser in order to request certificates and retrieve certificate revocation lists (CRLs).
- **Online Responder:** The Online Responder service decodes revocation status requests for specific certificates, evaluates the status of these certificates, and sends back a signed response containing the requested certificate status information.
- **Network Device Enrollment Service:** The Network Device Enrollment Service allows routers and other network devices that don't have domain accounts to obtain certificates.
- **TPM key attestation:** Lets the certification authority verify the private key is protected by a hardware-based TPM and that the TPM is one that the CA trusts. TPM key attestation prevents the certificate from being exported to an unauthorized device and can bind the user identity to the device.
- **Certificate Enrollment Policy Web Service:** The Certificate Enrollment Policy Web Service enables users and computers to obtain certificate enrollment policy information.
- **Certificate Enrollment Web Service:** Certificate Enrollment Web Service enables users and computers to perform certificate enrollment through a web service. Together with the Certificate Enrollment Policy Web Service, this enables policy-based certificate enrollment when the client computer isn't a member of a domain or when a domain member isn't connected to the domain.
- **Post-Quantum Cryptography (PQC) support:** AD CS supports Module-Lattice-Based Digital Signature Algorithm (ML-DSA), a NIST-standardized post-quantum digital signature algorithm. You can configure CAs, certificate templates, and Online Responders to use ML-DSA for signing operations. To learn more, see [Post-quantum cryptography in AD CS overview](post-quantum-cryptography-overview).

## Benefits

You can use AD CS to enhance security by binding the identity of a person, computer, or service to a corresponding private key. AD CS provides a cost-effective, efficient, and secure way to manage the distribution and use of certificates. In addition to binding of identities and private keys, AD CS also includes features that allow you to manage certificate enrollment and revocation.

Existing endpoint identity information in Active Directory is used to register certificates, allowing information to be automatically inserted into certificates. Active Directory group policies can also be used to designate which users and machines are allowed which types of certificates. Group policy configuration enables role-based or attribute-based access control.

Applications supported by AD CS include Secure/Multipurpose Internet Mail Extensions (S/MIME), secure wireless networks, virtual private network (VPN), Internet Protocol security (IPsec), Encrypting File System (EFS), smart card sign in, Secure Socket Layer/Transport Layer Security (SSL/TLS), and digital signatures.