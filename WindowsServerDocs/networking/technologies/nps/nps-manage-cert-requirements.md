---
layout: Conceptual
title: Configure Certificate Templates for PEAP and EAP requirements | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-manage-cert-requirements
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This article provides information about using certificates with Network Policy Server and Remote Access in Windows Server 2016.
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2025-01-16T00:00:00.0000000Z
ms.contributor: samyun
locale: en-us
document_id: 2237d85b-4b60-02bf-0ce2-09d803a75186
document_version_independent_id: ff569ede-822d-1d39-b233-a66a3541d32a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-manage-cert-requirements.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-manage-cert-requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-manage-cert-requirements.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e48481f2-2b9d-98f2-15b1-102e3c2626ed
---

# Configure Certificate Templates for PEAP and EAP requirements | Microsoft Learn

All certificates that are used for network access authentication with Extensible Authentication Protocol-Transport Layer Security (EAP-TLS), Protected Extensible Authentication Protocol-Transport Layer Security (PEAP-TLS), and PEAP-Microsoft Challenge Handshake Authentication Protocol version 2 (MS-CHAP v2) must meet the requirements for X.509 certificates and work for connections that use Secure Socket Layer/Transport Level Security (SSL/TLS). Both client and server certificates have additional requirements.

Important

This article provides instructions for configuring certificate templates. To use these instructions, you must deploy your own Public Key Infrastructure (PKI) with Active Directory Certificate Services (AD CS) as required.

## Minimum server certificate requirements

With PEAP-MS-CHAP v2, PEAP-TLS, or EAP-TLS as the authentication method, the NPS must use a server certificate that meets the minimum server certificate requirements.

Client computers can be configured to validate server certificates by using the **Validate server certificate** option on the client computer or in Group Policy.

The client computer accepts the authentication attempt of the server when the server certificate meets the following requirements:

- The Subject name contains a value. If you issue a certificate to your server running Network Policy Server (NPS) that has a blank Subject name, the certificate isn't available to authenticate your NPS. To configure the certificate template with a Subject name:

    1. Open Certificate Templates.
    2. In the details pane, right-click the certificate template that you want to change, and then select **Properties** .
    3. Select the **Subject Name** tab, and then select **Build from this Active Directory information**.
    4. In **Subject name format**, select a value other than **None**.
- The computer certificate on the server:

    - Chains to a trusted root certification authority (CA) that includes the `Server Authentication` purpose in EKU extensions (the object identifier (OID) for `Server Authentication` is `1.3.6.1.5.5.7.3.1`), and passes:

        - The checks performed by CryptoAPI
        - The checks specified in the remote access policy or network policy
- Configure the server certificate with the required cryptography setting:

    1. Open Certificate Templates.
    2. In the details pane, right-click the certificate template that you want to change, and then select **Properties**.
    3. Select the **Cryptography**tab and make sure to configure the following:
        - **Provider Category:** for example, **Key Storage Provider**
        - **Algorithm Name:** for example, **RSA**
        - **Providers:** for example, **Microsoft Software Key Storage Provider**
        - **Minimum key size:** for example, **2048**
        - **Hash Algorithm:** for example, **SHA256**
    4. Select **Next**.
- The Subject Alternative Name (SubjectAltName) extension, if used, must contain the DNS name of the server. To configure the certificate template with the Domain Name System (DNS) name of the enrolling server:

    1. Open Certificate Templates.
    2. In the details pane, right-click the certificate template that you want to change, and then select **Properties** .
    3. Select the **Subject Name** tab, and then select **Build from this Active Directory information**.
    4. In **Include this information in alternate subject name**, select **DNS name**.

When users use PEAP and EAP-TLS, NPS displays a list of all installed certificates in the computer certificate store, with the following exceptions:

- Certificates that don't contain the `Server Authentication` purpose in EKU extensions aren't displayed.
- Certificates that don't contain a Subject name aren't displayed.
- Registry-based and smart card-logon certificates aren't displayed.

For more information, see [Deploy Server Certificates for 802.1X Wired and Wireless Deployments](../../core-network-guide/cncg/server-certs/deploy-server-certificates-for-802.1x-wired-and-wireless-deployments).

## Minimum client certificate requirements

With EAP-TLS or PEAP-TLS, the server accepts the client authentication attempt when the certificate meets the following requirements:

- The client certificate is issued by an enterprise CA or mapped to a user or computer account in Active Directory Domain Services (AD DS).
- The user or computer certificate on the client:

    - Chains to a trusted root CA that includes the `Client Authentication` purpose in EKU extensions (the OID for `Client Authentication` is `1.3.6.1.5.5.7.3.2`), and passes:

        - The checks performed by CryptoAPI
        - The checks specified in the remote access policy or network policy
        - The certificate object identifier checks specified in NPS network policy.
- The 802.1X client doesn't use registry-based certificates that are either smart card-logon or password-protected certificates.
- For user certificates, the Subject Alternative Name (SubjectAltName) extension in the certificate contains the user principal name (UPN). To configure the UPN in a certificate template:

    1. Open Certificate Templates.
    2. In the details pane, right-click the certificate template that you want to change, and then select **Properties**.
    3. Select the **Subject Name** tab, and then select **Build from this Active Directory information**.
    4. In **Include this information in alternate subject name**, select **User principal name (UPN)**.
- For computer certificates, the Subject Alternative Name (SubjectAltName) extension in the certificate must contain the fully qualified domain name (FQDN) of the client, which is also called the *DNS name*. To configure this name in the certificate template:

    1. Open Certificate Templates.
    2. In the details pane, right-click the certificate template that you want to change, and then select **Properties**.
    3. Select the **Subject Name** tab, and then select **Build from this Active Directory information**.
    4. In **Include this information in alternate subject name**, select **DNS name**.

With PEAP-TLS and EAP-TLS, clients display a list of all installed certificates in the Certificates snap-in, with the following exceptions:

- Wireless clients don't display registry-based and smart card-logon certificates.
- Wireless clients and VPN clients don't display password-protected certificates.
- Certificates that don't contain the `Client Authentication` purpose in EKU extensions aren't displayed.