---
layout: Conceptual
title: What is Network Device Enrollment Service for Active Directory Certificate Services? | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/network-device-enrollment-service-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn about the role of Network Device Enrollment Service and how it works with certificates based on Simple Certificate Enrollment Protocol
author: robinharwood
ms.author: roharwoo
ms.topic: overview
ms.date: 2025-01-03T00:00:00.0000000Z
locale: en-us
document_id: e82c12e9-708d-ac5d-e4bc-3e62a4f72f26
document_version_independent_id: e82c12e9-708d-ac5d-e4bc-3e62a4f72f26
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/network-device-enrollment-service-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/network-device-enrollment-service-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/network-device-enrollment-service-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 4bc609ca-f577-5575-1d10-345856395fac
---

# What is Network Device Enrollment Service for Active Directory Certificate Services? | Microsoft Learn

The Network Device Enrollment Service (NDES) is one of the role services of Active Directory Certificate Services (AD CS). NDES acts as a Registration Authority to enable the software on routers and other network devices running without domain credentials to get certificates based on the Simple Certificate Enrollment Protocol (SCEP).

SCEP defines the communication protocol between network devices and a Registration Authority for certificate enrollment. It strives to support the secure issuance of certificates to network devices in a scalable manner, using existing technology in closed networks with trusted endpoints. For more information on SCEP, see [RFC 8894 Simple Certificate Enrollment Protocol](https://datatracker.ietf.org/doc/html/rfc8894).

## Understanding the Network Device Enrollment Service

SCEP is a solution to the problem of enabling network devices that don't run with domain credentials to enroll for x509 version 3 certificates from a Certification Authority (CA). NDES provides any network device with a private key and associated certificate issued by a CA. Applications on the device can use the key and its associated certificate to interact with other entities on the network. The most common use of an NDES-issued certificate on a network device is to authenticate the device in an IPSec session.

SCEP was developed to support the secure, scalable issuance of certificates to network devices by using existing certification authorities (CAs). The protocol supports CA and registration authority public key distribution, enrollment, and certificate revocation queries.

NDES performs the following functions:

- Generates and provides one-time enrollment passwords to administrators.
- Submits enrollment requests to the CA.
- Retrieves enrolled certificates from the CA and forwards them to the network device.

NDES is implemented as an Internet Server API (ISAPI) extension. It requires the Internet Information Services (IIS) role to be installed on the same computer. It doesn't require the CA to be installed on the same computer. The ISAPI extension runs in its own application pool, that is, SCEP. This application pool is created during setup and is configured to run with the credentials that were provided during setup.

The SCEP specification doesn't require devices to support TLS. However, the process of retrieving a one-time password from the service should be protected using TLS. Setup creates two virtual applications - one for the device and one for the administrator.

- Devices communication location`https://<hostname>/certsrv/mscep`
- Administrator enrollment password retrieval location `https://<hostname>/certsrv/mscep_admin`

Passwords are used by the service to authenticate the device before forwarding its enrollment request to the CA. Passwords are obtained through a call to the administration virtual application.

Enrolling certificates through Network Device Enrollment Service is a straightforward process:

1. Device obtains an RSA public-private key pair from the */certsrv/mscep* web endpoint.
2. Administrator obtains a password from the Network Device Enrollment Service.
3. Administrator sets device with password and sets it to trust the enterprise PKI */certserv/mscep\_admin* web endpoint.
4. Device configured to send enrollment request to NDES.
5. NDES signs enrollment request with Enrollment Agent certificate and sends it to the CA.
6. CA issues the certificate.
7. Device retrieves issued certificate from NDES.

## NDES configuration settings

NDES can be configured to run as either of the following after installing the NDES role service:

- A user account that is specified as a service account
- The built-in application pool identity of the Internet Information Services (IIS) computer