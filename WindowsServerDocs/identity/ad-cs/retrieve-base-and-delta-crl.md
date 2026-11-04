---
layout: Conceptual
title: Retrieve base & delta CRLs using Web Enrollment in AD CS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/retrieve-base-and-delta-crl
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to retrieve the current base and delta certificate revocation lists (CRLs) using Certification Authority Web Enrollment role service in Windows Server
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2023-09-04T00:00:00.0000000Z
locale: en-us
document_id: 9efc2e84-f5f1-eec4-03fe-ac73ed3e2e53
document_version_independent_id: 9efc2e84-f5f1-eec4-03fe-ac73ed3e2e53
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/retrieve-base-and-delta-crl.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/retrieve-base-and-delta-crl
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/retrieve-base-and-delta-crl.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae6f56e9-ba4c-cbdd-1598-e12e4c995689
---

# Retrieve base & delta CRLs using Web Enrollment in AD CS | Microsoft Learn

This article shows you how to retrieve the current base and delta certificate revocation lists (CRLs) using the Certification Authority (CA) Web Enrollment role service. The CA Web Enrollment role service provides a set of web pages that allow interaction with the Certification Authority role service. To learn more about Certification Authority Web Enrollment, see [What is the Certification Authority Role Service?](certification-authority-role).

## Prerequisites

Before you can retrieve base and delta CRLs, your computer must meet the following requirements:

- Have a server that is a domain member with the Certificate Enrollment Web Service installed.
- Client computers must be running Windows or Windows Server.

## Retrieve a certificate revocation list by using a web browser

1. Open your web browser and connect to `https://<servername>/certsrv`, where `<servername>` is the name of the server running the CA Web Enrollment role service.
2. Select **Download a CA certificate, certificate chain, or CRL**.
3. Select the encoding method that you want to use for the CRL, **DER** or **Base 64**.
4. Select one of the following actions:

    - **Download CA certificate**.
    - **Download CA certificate chain**.
    - **Download latest base CRL**.
    - **Download latest delta CRL**.

    Note

    The latest base CRL must already be installed for the delta CRL to function.
5. When the **File Download** dialog box appears, select **Save**. Select a folder on your computer to store the `.crl` file, and then select **Save**.
6. Open Windows Explorer and locate the `.crl` file you saved.
7. Right-click the `.cer` or `.crl` file and select **Install Certificate** or **Install CRL**, and then select **Next**.
8. When the Certificate Import Wizard opens, select **Automatically select the certificate store based on the type of certificate**.