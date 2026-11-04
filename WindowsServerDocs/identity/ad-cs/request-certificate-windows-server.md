---
layout: Conceptual
title: Request Certificates Using Web Enrollment in Active Directory Certificate Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/request-certificate-windows-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Request certificates easily with basic or advanced options using the Certification Authority Web Enrollment Role Service. Follow this guide to get started.
author: robinharwood
ms.topic: how-to
ms.author: roharwoo
ms.date: 2025-04-28T00:00:00.0000000Z
locale: en-us
document_id: 4814d3c0-3b52-ef58-d1fa-9374ac6486a3
document_version_independent_id: 4814d3c0-3b52-ef58-d1fa-9374ac6486a3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/request-certificate-windows-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/request-certificate-windows-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/request-certificate-windows-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 637a3be5-15b5-9098-f94c-52d543f28db5
---

# Request Certificates Using Web Enrollment in Active Directory Certificate Services | Microsoft Learn

This article explains how to request certificates using the Certification Authority (CA) Web Enrollment Role Service in Windows Server. The CA Web Enrollment role service provides web pages to interact with the Certification Authority role service. Learn more about the Certification Authority Web Enrollment role service in [What is the Certification Authority role service?](certification-authority-role).

## Prerequisites

Before you can submit a request, you must meet the following requirements:

- Have a server that is a domain member with the Certificate Enrollment Web Service installed.
- Client computers must be running Windows or Windows Server.

## Request a basic certificate

1. Using a web browser, connect to `https://<servername>/certsrv`, where `<servername>` is the host name of the computer running the CA Web Enrollment role service.
2. Select **Request a certificate**.
3. On the **Request a Certificate** page, select **User Certificate**.
4. On the **User Certificate Identifying Information** page, follow one of these steps:

    - If the message "No further identifying information is required. To complete your certificate, select Submit." appears, select **Submit**.
    - Enter your identifying information for the certificate request.
5. (Optional) Select **More Options** to specify the cryptographic service provider (CSP) and enable strong private key protection if needed. You receive a prompt every time you use the private key that is associated with the certificate.
6. Select **Submit**.
7. If you see the **Certificate Issued** web page, select **Download certificate chain**. Save the file to your hard disk drive, then import the certificate into your certificate store.

If you see the **Certificate Pending** web page, check the status of your request in the Check a pending certificate request section.

## Request a certificate with advanced options

1. Open a web browser and go to `https://<servername>/certsrv`, where `<servername>` is the hostname of the computer running the CA Web Enrollment role service.
2. Select **Request a certificate**.
3. Select **Advanced certificate request**.
4. Select **Create and submit a certificate request to this CA**.
5. Fill in the requested identifying information and other options that you require.
6. Select **Submit**.
7. If you see the **Certificate Issued** web page, select **Download certificate chain**. Save the file to your hard disk drive, then import the certificate into your certificate store.

If you see the **Certificate Pending** web page, you can check the status of your request in the following section.

### Check a pending certificate request

1. Using a web browser, open `https://<servername>/certsrv`, where `<servername>` is the hostname of the computer running the CA Web Enrollment role service.
2. Select **View the status of a pending certificate request**.
3. If there are no pending certificate requests, a message confirms there are no pending requests. Otherwise, select the certificate request that you want to check, and select **Next**.
4. Check the following pending certificate requests:

    - **Still pending**. Wait for the certification authority administrator to issue the certificate. To remove the certificate request, select **Remove**.
    - **Issued**. To install the certificate, select **Install this certificate**.
    - **Denied**. Contact the administrator of the certification authority for further information.