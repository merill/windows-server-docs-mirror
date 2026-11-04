---
layout: Conceptual
title: What is the Certification Authority Role Service in Windows Server? | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/certification-authority-role
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: You can use this article to understand the Active Directory Certificate Services Certification Authority role.
author: Orin-Thomas
ms.topic: concept-article
ms.author: orthomas
contributor: orthomas
ms.date: 2023-06-20T00:00:00.0000000Z
locale: en-us
document_id: 65045d25-b35e-275a-1119-88705dc6aeb8
document_version_independent_id: 65045d25-b35e-275a-1119-88705dc6aeb8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/certification-authority-role.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/certification-authority-role
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/certification-authority-role.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 2c08945e-d4ff-251e-e144-e981d14880b5
---

# What is the Certification Authority Role Service in Windows Server? | Microsoft Learn

This article provides information on the Certification Authority role service for Active Directory Certificate Services when deployed on the Windows Server operating system.

A certification authority (CA) is responsible for attesting to the identity of users, computers, and organizations. The CA authenticates an entity and vouches for that identity by issuing a digitally signed certificate. The CA can also manage, revoke, and renew certificates.

A certification authority can be:

- An organization that vouches for the identity of an end user.
- A server that is used by the organization to issue and manage certificates.

By installing the Certification Authority role service of Active Directory Certificate Services (AD CS), you can configure your Windows server to act as a CA.

## Understanding certification authority types

Windows Server supports four different types of CA:

- Enterprise Root CA.
- Enterprise Subordinate CA.
- Standalone Root CA.
- Standalone Subordinate CA.

## Enterprise and Standalone certification authorities

Enterprise CAs are integrated with Active Directory Domain Services (AD DS). They publish certificates and certificate revocation lists (CRLs) to AD DS. Enterprise CA's use information that is stored in AD DS, including user accounts and security groups, to approve or deny certificate requests. Enterprise CAs use certificate templates. When a certificate is issued, the Enterprise CA uses information in the certificate template to generate a certificate with the appropriate attributes for that certificate type.

If you want to enable automated certificate approval and automatic user certificate enrollment, use Enterprise CAs to issue certificates. These features are available only when the CA infrastructure is integrated with Active Directory. Additionally, only Enterprise CAs can issue certificates that enable smart card sign-in, because this process requires that smart card certificates are mapped automatically to the user accounts in Active Directory.

Stand-alone CAs don't require AD DS, and they don't use certificate templates. If you use stand-alone CAs, all information about the requested certificate type must be included in the certificate request. By default, all certificate requests that are submitted to stand-alone CAs are held in a pending queue until a CA administrator approves them. You can configure stand-alone CAs to issue certificates automatically upon request, but it's less secure and it's not recommended because requests aren't authenticated.

You must use stand-alone CAs to issue certificates when you're using a non-Microsoft directory service or when AD DS isn't available. You can use both enterprise and stand-alone certification authorities in your organization.

## Root and subordinate certification authorities

Enterprise and stand-alone CAs can be configured as root CAs or as subordinate CAs. Subordinate CAs can further be configured as intermediate CAs (also referred to as a policy CA) or issuing CAs

A root CA is the CA that is at the top of a certification hierarchy, where all certificate chains terminate. When the root CA certificate is present on the client, the root CA is trusted unconditionally. Whether you use enterprise or stand-alone CAs, you need to designate a root CA.

Since the root CA is the top CA in the certification hierarchy, the Subject field of the certificate has the same value as the Issuer field. Likewise, because the certificate chain terminates when it reaches a self-signed CA, all self-signed CAs are root CAs. The decision to designate a CA as a trusted root CA can be made at the enterprise level or locally by the individual IT administrator.

A root CA serves as the foundation upon which you base your certification authority trust model. It guarantees that the subject's public key corresponds to the identity information shown in the subject field of the certificates it issues. Different CAs might also verify this relationship by using different standards; therefore, it's important to understand the policies and procedures of the root certification authority before choosing to trust that authority to verify public keys.

The root CA is the most important CA in your hierarchy. If your root CA is compromised, all CAs in the hierarchy and all certificates issued from it are considered compromised. You can maximize the security of the root CA by keeping it disconnected from the network and by using subordinate CAs to issue certificates to other subordinate CAs or to end users. A disconnected root CA is also known as an Offline root CA.

CAs that aren't root CAs are considered subordinate. The first subordinate CA in a hierarchy obtains its CA certificate from the root CA. This first subordinate CA can use this key to issue certificates that verify the integrity of another subordinate CA. These higher subordinate CAs are referred to as intermediate CAs. An intermediate CA is subordinate to a root CA, but it serves as a higher certifying authority to one or more subordinate CAs.

An intermediate CA is often referred to as a policy CA because it's typically used to separate classes of certificates that are distinguished through policies. For example, policy separation includes the level of assurance that a CA provides or the geographical location of the CA to distinguish different end-entity populations. A policy CA can be online or offline.

## Certification authority private keys

The private key is part of the CA identity, and it must be protected from compromise. Many organizations protect CA private keys by using a hardware security module (HSM). If an HSM isn't used, the private key is stored on the CA computer.

Offline CAs should be stored in secure locations and not connected to the network. Issuing CAs use their private keys when issuing certificates, so the private key must be accessible (online) while the CA is in operation. In all cases, the CA and its private key on the CA should be physically protected.

## Hardware security modules

Using a hardware security module (HSM) can enhance the security of your CA and Private Key Infrastructure (PKI).

An HSM is a dedicated hardware device that is managed separately from the operating system. HSMs provide a secure hardware store for CA keys, in addition to a dedicated cryptographic processor to accelerate signing and encrypting operations. The operating system utilizes the HSM through the CryptoAPI interfaces, and the HSM functions as a cryptographic service provider (CSP) device.

HSMs typically are PCI adapters, but they're also available as network-based appliances, serial devices, and USB devices. If an organization plans to implement two or more CAs, you can install a single network-based HSM and share it among multiple CAs.

HSMs must be installed and configured before you set up any CAs with keys that need to be stored on the HSM.