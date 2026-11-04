---
layout: Conceptual
title: Copy the CA Certificate and CRL to the Virtual Directory | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/server-certs/copy-the-ca-certificate-and-crl-to-the-virtual-directory
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to copy the Certificate Revocation List and Enterprise root CA certificate from your certification authority to a virtual directory on your Web server, and to ensure that AD CS is configured correctly.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-19T00:00:00.0000000Z
locale: en-us
document_id: 52129502-f4ab-7687-e1e2-fdb41451c041
document_version_independent_id: 12ffc4aa-27df-fb3a-b806-d32f42f90eb9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Copy-the-CA-Certificate-and-CRL-to-the-Virtual-Directory.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/server-certs/copy-the-ca-certificate-and-crl-to-the-virtual-directory
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Copy-the-CA-Certificate-and-CRL-to-the-Virtual-Directory.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 8a2dab70-bea1-d262-b32a-81cd56ada4ed
---

# Copy the CA Certificate and CRL to the Virtual Directory | Microsoft Learn

You can use this procedure to copy the Certificate Revocation List and Enterprise root CA certificate from your certification authority to a virtual directory on your Web server, and to ensure that AD CS is configured correctly. Before running the commands below, ensure that you replace directory and server names with those that are appropriate for your deployment.

To perform this procedure you must be a member of **Domain Admins**.

#### To copy the certificate revocation list from CA1 to WEB1

1. On CA1, run Windows PowerShell as an Administrator, and then publish the CRL with the following command:

    - Type `certutil -crl`, and then press ENTER.
    - To copy the CA1 certificate to the file share on your Web server, type `copy C:\Windows\system32\certsrv\certenroll\*.crt \\WEB1\pki`, and then press ENTER.
    - To copy the certificate revocation lists to the file share on your Web server, type `copy C:\Windows\system32\certsrv\certenroll\*.crl \\WEB1\pki`, and then press ENTER.
2. To verify that your CDP and AIA extension locations are correctly configured, type `pkiview.msc`, and then press ENTER. The pkiview Enterprise PKI MMC opens.
3. In the left pane, click your CA name.

    For example, if your CA name is corp-CA1-CA, click **corp-CA1-CA**.
4. In the Status column of the results pane, verify that the values for the following shows **OK**:

    - **CA Certificate**
    - **AIA Location #1**
    - **CDP Location #1**

Tip

If **Status** for any item is not **OK**, do the following:

- Open the share on your Web server to verify that the certificate and certificate revocation list files were successfully copied to the share. If they were not successfully copied to the share, modify your copy commands with the correct file source and share destination and run the commands again.
- Verify that you have entered the correct locations for the CDP and AIA on the CA Extensions tab. Ensure that there are no extra spaces or other characters in the locations that you have provided.
- Verify that you copied the CRL and CA certificate to the correct location on your Web server, and that the location matches the location you provided for the CDP and AIA locations on the CA.
- Verify that you correctly configured permissions for the virtual folder where the CA certificate and CRL are stored.