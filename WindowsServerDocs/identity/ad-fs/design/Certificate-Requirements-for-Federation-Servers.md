---
layout: Conceptual
title: Certificate Requirements for Federation Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/certificate-requirements-for-federation-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Certificate Requirements for Federation Servers'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 40d0e7ee-a10e-6daf-32ad-d16621949c71
document_version_independent_id: ef844ba3-6755-25c2-2ad1-73dc42f945df
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Certificate-Requirements-for-Federation-Servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/certificate-requirements-for-federation-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Certificate-Requirements-for-Federation-Servers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: c83d3bec-15ab-2962-dc5d-3a040e64579b
---

# Certificate Requirements for Federation Servers | Microsoft Learn

In any Active Directory Federation Services (AD FS) design, various certificates must be used to secure communication and facilitate user authentications between Internet clients and federation servers. Each federation server must have a service communication certificate and a token-signing certificate before it can participate in AD FS communications. The following table describes the certificate types that are associated with federation server.

| Certificate type | Description |
| --- | --- |
| Token-signing certificate | A token-signing certificate is an X509 certificate. Federation servers use associated public/private key pairs to digitally sign all security tokens that they produce. This includes the signing of published federation metadata and artifact resolution requests.<br>You can have multiple token-signing certificates configured in the AD FS Management snap-in to allow for certificate rollover when one certificate is close to expiring. By default, all the certificates in the list are published, but only the primary token-signing certificate is used by AD FS to actually sign tokens. All certificates that you select must have a corresponding private key.<br><br>For more information, see [Token-Signing Certificates](token-signing-certificates) and [Add a Token-Signing Certificate](../deployment/add-a-token-signing-certificate). |
| Service communication certificate | Federation servers use a server authentication certificate, also known as a service communication for Windows Communication Foundation (WCF) Message Security. By default, this is the same certificate that a federation server uses as the Secure Sockets Layer (SSL) certificate in Internet Information Services (IIS). **Note:** The AD FS Management snap-in refers to server authentication certificates for federation servers as service communication certificates.<br>For more information, see [Service Communications Certificates](service-communications-certificates) and [Set a Service Communications Certificate](../deployment/set-a-service-communications-certificate).<br><br>Because the service communication certificate must be trusted by client computers, we recommend that you use a certificate that is signed by a trusted certification authority (CA). All certificates that you select must have a corresponding private key. |
| Secure Sockets Layer (SSL) certificate | Federation servers use an SSL certificate to secure Web services traffic for SSL communication with Web clients and with federation server proxies.<br>Because the SSL certificate must be trusted by client computers, we recommend that you use a certificate that is signed by a trusted CA. All certificates that you select must have a corresponding private key. |
| Token-decryption certificate | This certificate is used to decrypt tokens that are received by this federation server.<br>You can have multiple decryption certificates. This makes it possible for a resource federation server to be able to decrypt tokens that are issued with an older certificate after a new certificate is set as the primary decryption certificate. All certificates can be used for decryption, but only the primary token-decrypting certificate is actually published in federation metadata. All certificates that you select must have a corresponding private key.<br><br>For more information, see [Add a Token-Decrypting Certificate](../deployment/add-a-token-decrypting-certificate). |

You can request and install an SSL certificate or service communication certificate by requesting a service communication certificate through the Microsoft Management Console (MMC) snap-in for IIS. For more general information about using SSL certificates, see [IIS 7.0: Configuring Secure Sockets Layer in IIS 7.0](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771438%28v=ws.10%29) and [IIS 7.0: Configuring Server Certificates in IIS 7.0](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230%28v=ws.10%29) .

Note

In AD FS you can change the Secure Hash Algorithm (SHA) level that is used for digital signatures to either SHA-1 or SHA-256 (more secure). AD FSdoes not support the use of certificates with other hash methods, such as MD5 (the default hash algorithm that is used with the Makecert.exe command-line tool). As a security best practice, we recommend that you use SHA-256 (which is set by default) for all signatures. SHA-1 is recommended for use only in scenarios in which you must interoperate with a product that does not support communications using SHA-256, such as a non-Microsoft product or AD FS 1. *x*.

## Determining your CA strategy

AD FS does not require that certificates be issued by a CA. However, the SSL certificate (the certificate that is also used by default as the service communications certificate) must be trusted by the AD FS clients. We recommend that you not use self-signed certificates for these certificate types.

Important

Use of self-signed, SSL certificates in a production environment can allow a malicious user in an account partner organization to take control of federation servers in a resource partner organization. This security risk exists because self-signed certificates are root certificates. They must be added to the trusted root store of another federation server (for example, the resource federation server), which can leave that server vulnerable to attack.

After you receive a certificate from a CA, make sure that all certificates are imported into the personal certificate store of the local computer. You can import certificates to the personal store with the Certificates MMC snap-in.

As an alternative to using the Certificates snap-in, you can also import the SSL certificate with the IIS Manager snap-in at the time that you assign the SSL certificate to the default Web site. For more information, see [Import a Server Authentication Certificate to the Default Web Site](../deployment/import-a-server-authentication-certificate-to-the-default-web-site).

Note

Before you install the AD FS software on the computer that will become the federation server, make sure that both certificates are in the Local Computer personal certificate store and that the SSL certificate is assigned to the Default Web Site. For more information about the order of the tasks that are required to set up a federation server, see [Checklist: Setting Up a Federation Server](../deployment/checklist--setting-up-a-federation-server).

Depending on your security and budget requirements, carefully consider which of your certificates will be obtained by a public CA or a corporate CA. The following figure shows the recommended CA issuers for a given certificate type. This recommendation reflects a best-practice approach regarding security and cost.

![cert requirements](media/adfs2_fedserver_certstory_1.png)

## Certificate revocation lists

If any certificate that you use has CRLs, the server with the configured certificate must be able to contact the server that distributes the CRLs.