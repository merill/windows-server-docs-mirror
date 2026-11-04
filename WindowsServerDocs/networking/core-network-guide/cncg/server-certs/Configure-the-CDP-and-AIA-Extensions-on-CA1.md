---
layout: Conceptual
title: Configure the CDP and AIA Extensions on CA1 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-cdp-and-aia-extensions-on-ca1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to configure the Certificate Revocation List (CRL) Distribution Point (CDP) and the Authority Information Access (AIA) settings on CA1.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-26T00:00:00.0000000Z
locale: en-us
document_id: 44d61775-ac5e-36e3-7dec-05cf281a6604
document_version_independent_id: 826fa35d-c85b-c92b-51cb-f1b8ef3bfab4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Configure-the-CDP-and-AIA-Extensions-on-CA1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/server-certs/configure-the-cdp-and-aia-extensions-on-ca1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Configure-the-CDP-and-AIA-Extensions-on-CA1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 7ccdbc5f-ba5a-17db-1351-984873a8815a
---

# Configure the CDP and AIA Extensions on CA1 | Microsoft Learn

You can use this procedure to configure the Certificate Revocation List (CRL) Distribution Point (CDP) and the Authority Information Access (AIA) settings on CA1.

To perform this procedure, you must be a member of Domain Admins.

#### To configure the CDP and AIA extensions on CA1

1. In Server Manager, click **Tools** and then click **Certification Authority**.
2. In the Certification Authority console tree, right-click **corp-CA1-CA**, and then click **Properties**.

    Note

    The name of your CA is different if you did not name the computer CA1 and your domain name is different than the one in this example. The CA name is in the format *domain*-*CAComputerName*-CA.
3. Click the **Extensions** tab. Ensure that **Select extension** is set to **CRL Distribution Point (CDP)**, and in the **Specify locations from which users can obtain a certificate revocation list (CRL)**, do the following:

    1. Select the entry `file://\\<ServerDNSName>\CertEnroll\<CaName><CRLNameSuffix><DeltaCRLAllowed>.crl`, and then click **Remove**. In **Confirm removal**, click **Yes**.
    2. Select the entry `http://<ServerDNSName>/CertEnroll/<CaName><CRLNameSuffix><DeltaCRLAllowed>.crl`, and then click **Remove**. In **Confirm removal**, click **Yes**.
    3. Select the entry that starts with the path `ldap:///CN=<CATruncatedName><CRLNameSuffix>,CN=<ServerShortName>`, and then click **Remove**. In **Confirm removal**, click **Yes**.
4. In **Specify locations from which users can obtain a certificate revocation list (CRL)**, click **Add**. The **Add Location** dialog box opens.
5. In **Add Location**, in **Location**, type `http://pki.corp.contoso.com/pki/<CaName><CRLNameSuffix><DeltaCRLAllowed>.crl`, and then click **OK**. This returns you to the CA properties dialog box.
6. On the **Extensions** tab, select the following check boxes:

    - **Include in CRLs. Clients use this to find the Delta CRL locations**
    - **Include in the CDP extension of issued certificates**
7. In **Specify locations from which users can obtain a certificate revocation list (CRL)**, click **Add**. The **Add Location** dialog box opens.
8. In **Add Location**, in **Location**, type `file://\\pki.corp.contoso.com\pki\<CaName><CRLNameSuffix><DeltaCRLAllowed>.crl`, and then click **OK**. This returns you to the CA properties dialog box.
9. On the **Extensions** tab, select the following check boxes:

    - **Publish CRLs to this location**
    - **Publish Delta CRLs to this location**
10. Change **Select extension** to **Authority Information Access (AIA)**, and in the **Specify locations from which users can obtain a certificate for this CA**, complete the following steps:

    1. Select the entry that starts with the path `ldap:///CN=<CATruncatedName>,CN=AIA,CN=Public Key Services`, and then click **Remove**. In **Confirm removal**, click **Yes**.
    2. Select the entry `http://<ServerDNSName>/CertEnroll/<ServerDNSName>_<CaName><CertificateName>.crt`, and then click **Remove**. In **Confirm removal**, click **Yes**.
    3. Select the entry `file://\\<ServerDNSName>\CertEnroll\<ServerDNSName><CaName><CertificateName>.crt`, and then click **Remove**. In **Confirm removal**, click **Yes**.
11. In **Specify locations from which users can obtain the certificate for this CA**, click **Add**. The **Add Location** dialog box opens.
12. In **Add Location**, in **Location**, type `http://pki.corp.contoso.com/pki/<ServerDNSName>_<CaName><CertificateName>.crt`, and then click **OK**. This returns you to the CA properties dialog box.
13. On the **Extensions** tab, select **Include in the AIA of issued certificates**.
14. When prompted to restart Active Directory Certificate Services, click **No**. You will restart the service later.