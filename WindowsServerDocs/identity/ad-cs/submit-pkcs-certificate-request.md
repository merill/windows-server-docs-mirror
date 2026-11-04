---
layout: Conceptual
title: 'Submit certificate requests to AD CS using a PKCS #10 or PKCS #7 file in Windows Server | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/submit-pkcs-certificate-request
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn how to submit a certificate in CA Web Enrollment role service by using a PKCS #10 file or a PKCS #7 file in Windows Server'
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2023-09-09T00:00:00.0000000Z
locale: en-us
document_id: 14255e43-1554-27fb-46f9-991c1e149935
document_version_independent_id: 14255e43-1554-27fb-46f9-991c1e149935
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/submit-pkcs-certificate-request.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/submit-pkcs-certificate-request
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/submit-pkcs-certificate-request.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: ce6772ca-957d-d54a-6118-f590ab419069
---

# Submit certificate requests to AD CS using a PKCS #10 or PKCS #7 file in Windows Server | Microsoft Learn

This article shows you how to submit a certificate in Certification Authority (CA) Web Enrollment role service by using a PKCS #10 file or a PKCS #7 file. The CA Web Enrollment role service provides a set of web pages that allow interaction with the Certification Authority role service. For more information about the CA Web Enrollment role service, see [Certification Authority Web Enrollment Guidance](certification-authority-role).

## Prerequisites

Before you can submit a request, you must meet the following requirements:

- Have a server that is a domain member with the Certificate Enrollment Web Service installed.
- Client computers must be running Windows or Windows Server.

## Submit a certificate request by using a PKCS #10 or PKCS #7 file

1. Using a web browser, connect to `https://<servername>/certsrv`, where `<servername>` is the name of the computer running the CA Web Enrollment role service.
2. Select **Request a certificate**, and then select **Advanced certificate request**.
3. Select **Submit a certificate request using a base-64-encoded CMC or PKCS #10 file, or submit a renewal request by using a base-64-encoded PKCS #7 file**.
4. In Notepad, select **File**, select **Open**, select the PKCS #10 or PKCS #7 file.
5. Select **Edit**, select **Select all**, select **Edit**, and then select **Copy**.
6. Return to the web page, select the **Saved request** scroll box. Select **Edit**, and then select **Paste** to paste the contents of certificate request into the scroll box.
7. If you're connected to an enterprise CA, choose the certificate template that you want to use. By default, the appropriate template is named **Subordinate Certification Authority**.
8. If you have any attributes to add to the certificate request, enter them into **Additional Attributes**.
9. Select **Submit**.
10. If you see the **Certificate Issued** web page, select **Download certificate chain**. Choose to save the file to your hard disk drive, and then import the certificate into your certificate store.

If you see the **Certificate Pending** web page, you can check the status of your request in the following section.

## Check pending certificate requests

1. Using a web browser, open `https://<servername>/certsrv`, where `<servername>` is the hostname of the computer running the CA Web Enrollment role service.
2. Select **View the status of a pending certificate request**.
3. If there are no pending certificate requests, a message appears to confirm there are no request. Otherwise, select the certificate request that you want to check, and select **Next**.
4. Check the following pending certificate requests:

    - **Still pending**. You must wait for the administrator of the certification authority to issue the certificate. To remove the certificate request, select **Remove**.
    - **Issued**. To install the certificate, select **Install this certificate**.
    - **Denied**. Contact the administrator of the certification authority for further information.