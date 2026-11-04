---
layout: Conceptual
title: Add a Token-Decrypting Certificate | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/add-a-token-decrypting-certificate
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Add a Token-Decrypting Certificate'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: aff7e959-c8ed-c5ef-1284-c408130b2f54
document_version_independent_id: 0f8d1c0f-0356-a8f5-fc39-922aae37e3f6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Add-a-Token-Decrypting-Certificate.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/add-a-token-decrypting-certificate
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Add-a-Token-Decrypting-Certificate.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: f0e2ffb5-daee-b5f4-713b-5ed8b7ac25db
---

# Add a Token-Decrypting Certificate | Microsoft Learn

Federation servers use a token-decryption certificate when a relying party federation server must decrypt tokens that are issued with an older certificate after a new certificate is set as the primary decryption certificate. Active Directory Federation Services (AD FS) uses the Secure Sockets Layer (SSL) certificate for Internet Information Services (IIS) as the default decryption certificate.

Caution

Certificates used for token-decrypting are critical to the stability of the Federation Service. Because loss or unplanned removal of any certificates configured for this purpose can disrupt service, you should backup any certificates configured for this purpose.

You can use the following procedure to add the token-decrypting certificate to the AD FS Management snap-in from a file that you have exported.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29) (http://go.microsoft.com/fwlink/?LinkId=83477).

### To add a token-decrypting certificate

1. On the **Start** screen, type**AD FS Management**, and then press ENTER.
2. In the console tree, double-click **Service**, and then click **Certificates**.
3. In the **Actions** pane, click the **Add Token-Decrypting Certificate** link.
4. In the **Browse for Certificate file** dialog box, navigate to the certificate file that you want to add, select the certificate file, and then click **Open**.

## Additional references

[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)

[Certificate Requirements for Federation Servers](../design/certificate-requirements-for-federation-servers)