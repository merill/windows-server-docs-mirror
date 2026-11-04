---
layout: Conceptual
title: Certificate Requirements for Federation Server Proxies | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/certificate-requirements-for-federation-server-proxies
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Certificate Requirements for Federation Server Proxies'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: c8b82e82-f283-facc-8fb8-54defecf6276
document_version_independent_id: 7390ec00-8f0c-3b86-a96b-5436ebbc97b9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Certificate-Requirements-for-Federation-Server-Proxies.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/certificate-requirements-for-federation-server-proxies
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Certificate-Requirements-for-Federation-Server-Proxies.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 8fa12ff5-0cf8-e683-5f9f-40a82bcde7d1
---

# Certificate Requirements for Federation Server Proxies | Microsoft Learn

Servers that are running in the federation server proxy role in Active Directory Federation Services (AD FS) are required to use Secure Sockets Layer (SSL) server authentication certificates. Federation server proxies use SSL server authentication certificates to secure Web server traffic communication with Web clients.

Federation server proxies are usually exposed to computers on the Internet that are not included in your enterprise public key infrastructure (PKI). Therefore, use a server authentication certificate that is issued by a public (third-party) certification authority (CA), for example, VeriSign.

When you have a federation server proxy farm, all federation server proxy computers must use the same server authentication certificate. For more information, see [When to Create a Federation Server Proxy Farm](when-to-create-a-federation-server-proxy-farm).

It is important to verify that the subject name in the server authentication certificate matches the Federation Service name value that is specified in the AD FS Management snap-in. To locate this value, open the snap-in, right-click **Service**, click **Edit Federation Service Properties**, and then find the value in **Federation Service name** text box.

For general information about using SSL certificates, see Configuring Secure Sockets Layer in IIS 7.0 ([http://go.microsoft.com/fwlink/?LinkID=108544](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771438%28v=ws.10%29)) and Configuring Server Certificates in IIS 7.0 ([http://go.microsoft.com/fwlink/?LinkID=108545](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230%28v=ws.10%29)).

Note

Client authentication certificates are not required for AD FS federation server proxies.

If any certificate that you use has certificate revocation lists (CRLs), the server with the configured certificate must be able to contact the server that distributes the CRLs. The type of CRL determines what ports are used.