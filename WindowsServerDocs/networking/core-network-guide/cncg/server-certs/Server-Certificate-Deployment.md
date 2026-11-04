---
layout: Conceptual
title: Server Certificate Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/server-certs/server-certificate-deployment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn about the steps you have to carry out to install an enterprise root certification authority and to deploy server certificates for use with PEAP and EAP.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: d964fce6-1244-d88a-c38c-bc7193d939fe
document_version_independent_id: 59f5f3d2-600f-21e5-2aba-44570e66c115
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Server-Certificate-Deployment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/server-certs/server-certificate-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Server-Certificate-Deployment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 602eac59-e1d8-542f-b0f2-5e268a9e926e
---

# Server Certificate Deployment | Microsoft Learn

Follow these steps to install an enterprise root certification authority (CA) and to deploy server certificates for use with PEAP and EAP.

Important

Before you install Active Directory Certificate Services, you must name the computer, configure the computer with a static IP address, and join the computer to the domain. After you install AD CS, you cannot change the computer name or the domain membership of the computer, however you can change the IP address if needed. For more information on how to accomplish these tasks, see the Windows Server® 2016 [Core Network Guide](../../core-network-guide).

- [Install the Web Server WEB1](install-the-web-server-web1)
- [Create an alias (CNAME) record in DNS for WEB1](create-an-alias-cname-record-in-dns-for-web1)
- [Configure WEB1 to distribute Certificate Revocation Lists (CRLs)](configure-web1-to-distribute-certificate-revocation-lists)
- [Prepare the CAPolicy inf file](prepare-the-capolicy-inf-file)
- [Install the Certification Authority](install-the-certification-authority)
- [Configure the CDP and AIA extensions on CA1](configure-the-cdp-and-aia-extensions-on-ca1)
- [Copy the CA certificate and CRL to the virtual directory](copy-the-ca-certificate-and-crl-to-the-virtual-directory)
- [Configure the server certificate template](configure-the-server-certificate-template)
- [Configure server certificate autoenrollment](configure-server-certificate-autoenrollment)
- [Refresh Group Policy](refresh-group-policy)
- [Verify Server Enrollment of a Server Certificate](verify-server-enrollment-of-a-server-certificate)

Note

The procedures in this guide do not include instructions for cases in which the **User Account Control** dialog box opens to request your permission to continue. If this dialog box opens while you are performing the procedures in this guide, and if the dialog box was opened in response to your actions, click **Continue**.