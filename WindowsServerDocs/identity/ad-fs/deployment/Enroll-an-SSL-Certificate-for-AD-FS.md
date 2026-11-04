---
layout: Conceptual
title: Enroll an SSL Certificate for AD FS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/enroll-an-ssl-certificate-for-ad-fs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Enroll an SSL Certificate for AD FS'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 5ddab1b2-3b53-d52b-8205-82bd40685f31
document_version_independent_id: 65cc6b6f-c87e-3d1d-5f4c-1d2b921084b0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Enroll-an-SSL-Certificate-for-AD-FS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/enroll-an-ssl-certificate-for-ad-fs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Enroll-an-SSL-Certificate-for-AD-FS.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 54721e82-1c1d-32d7-4f5e-91066517efc6
---

# Enroll an SSL Certificate for AD FS | Microsoft Learn

Active Directory Federation Services (AD FS) requires a certificate for Secure Socket Layer (SSL) server authentication on each federation server in your federation server farm. The same certificate can be used on each federation server in a farm. You must have both the certificate and its private key available. For example, if you have the certificate and its private key in a .pfx file, you can import the file directly into the Active Directory Federation Services Configuration Wizard. This SSL certificate must contain the following:

1. The subject name and subject alternative name must contain your federation service name, such as fs.contoso.com.
2. The subject alternative name must contain the value **enterpriseregistration** that is followed by the User Principal Name (UPN) suffix of your organization, for example, **enterpriseregistration.corp.contoso.com**.

    Warning

    Specify the subject alternative name if you plan to enable the Device Registration Service (DRS) for Workplace Join.

Important

If your organization uses multiple UPN suffixes, and you plan to enable the DRS, the SSL certificate must contain a subject alternative name entry for each suffix.