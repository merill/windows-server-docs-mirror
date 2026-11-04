---
layout: Conceptual
title: Add a Token-Signing Certificate | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/add-a-token-signing-certificate
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Add a Token-Signing Certificate'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: acf03462-a52c-144e-4f8c-da9572549e4f
document_version_independent_id: 052d9c3b-8fcd-ffb2-5fdc-adfafcbdb67b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Add-a-Token-Signing-Certificate.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/add-a-token-signing-certificate
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Add-a-Token-Signing-Certificate.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 9776bd6a-2b89-94e5-1120-3795d8cdbf33
---

# Add a Token-Signing Certificate | Microsoft Learn

Federation servers in Active Directory Federation Services (AD FS) require token-signing certificates to prevent attackers from altering or counterfeiting security tokens in an attempt to gain unauthorized access to federated resources. Every token-signing certificate contains cryptographic private keys and public keys that are used to digitally sign (by means of the private key) a security token. Later, after these keys are received by a partner federation server, they validate the authenticity (by means of the public key) of the encrypted security token.

Caution

Certificates used for token-signing are critical to the stability of the Federation Service. Because loss or unplanned removal of any certificates configured for this purpose can disrupt service, you should backup any certificates configured for this purpose.

The token-signing certificate should chain to a trusted root in the Federation Service. You can use the following procedure to add the token-signing certificate to the AD FS Management snap-in from a file that you have exported.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29) (http://go.microsoft.com/fwlink/?LinkId=83477).

### To add a token-signing certificate

1. On the **Start** screen, type**AD FS Management**, and then press ENTER.
2. In the console tree, double-click **Service**, and then click **Certificates**.
3. In the **Actions** pane, click the **Add Token-Signing Certificate** link.
4. In the **Browse for Certificate file** dialog box, navigate to the certificate file that you want to add, select the certificate file, and then click **Open**.

## Additional references

[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)

[Certificate Requirements for Federation Servers](../design/certificate-requirements-for-federation-servers)