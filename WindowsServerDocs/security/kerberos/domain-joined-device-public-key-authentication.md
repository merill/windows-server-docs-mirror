---
layout: Conceptual
title: Domain-joined Device Public Key Authentication | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/kerberos/domain-joined-device-public-key-authentication
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Domain-joined Device Public Key Authentication'
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
locale: en-us
document_id: 916dd759-c564-2f27-95b1-896d287400c9
document_version_independent_id: 91ce2b56-77a2-fc0b-c576-9856f4074dff
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/kerberos/domain-joined-device-public-key-authentication.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/kerberos/domain-joined-device-public-key-authentication
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/kerberos/domain-joined-device-public-key-authentication.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f9cf537e-3e5a-4f31-a8e2-d06c28985eda
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b0200c40-0bea-4a73-a79b-8c68e19d3d16
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 7246a37e-1e5e-fed2-c9a9-65747a86091d
---

# Domain-joined Device Public Key Authentication | Microsoft Learn

Kerberos added support for domain-joined devices to sign-in using a certificate beginning with Windows Server 2012 and Windows 8. This change allows 3rd party vendors to create solutions to provision and initialize certificates for domain-joined devices to use for domain authentication.

## Automatic public key provisioning

Beginning with Windows 10 version 1507 and Windows Server 2016, domain-joined devices automatically provision a bound public key to a Windows Server 2016 domain controller (DC). Once a key is provisioned, then Windows can use public key authentication to the domain.

### Key generation

If the device is running Credential Guard, then a public/private key pair is created protected by Credential Guard.

If Credential Guard is not available and a TPM is, then a public/private key pair is created protected by the TPM.

If neither is available, then a key pair is not generated and the device can only authenticate using password.

### Provisioning computer account public key

When Windows starts up, it checks if a public key is provisioned for its computer account. If not, then it generates a bound public key and configures it for its account in AD using a Windows Server 2016 or higher DC. If all the DCs are down-level, then no key is provisioned.

### Configuring device to only use public key

If the Group Policy setting **Support for device authentication using certificate** is set to **Force**, then the device needs to find a DC that runs Windows Server 2016 or later to authenticate. The setting is under Administrative Templates &gt; System &gt; Kerberos.

### Configuring device to only use password

If the Group Policy setting **Support for device authentication using certificate** is disabled, then password is always used. The setting is under Administrative Templates &gt; System &gt; Kerberos.

## Domain-joined device authentication using public key

When Windows has a certificate for the domain-joined device, Kerberos first authenticates using the certificate and on failure retries with password. This allows the device to authenticate to down-level DCs.

Since the automatically provisioned public keys have a self-signed certificate, certificate validation fails on domain controllers that do not support Key Trust account mapping. By default, Windows retries authentication using the device's domain password.