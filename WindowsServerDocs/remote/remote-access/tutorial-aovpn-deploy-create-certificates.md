---
layout: Conceptual
title: 'Tutorial: Configure Certificate Authority Templates for Always On VPN | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/tutorial-aovpn-deploy-create-certificates
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to create certificate templates and enroll and validate certificates for users, VPN server, and NPS server to use with Always On VPN connections.
ms.topic: tutorial
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-08T00:00:00.0000000Z
locale: en-us
document_id: 3c6178f2-5716-460e-5ed1-66d5fb8c7022
document_version_independent_id: 3c6178f2-5716-460e-5ed1-66d5fb8c7022
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/tutorial-aovpn-deploy-create-certificates.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/tutorial-aovpn-deploy-create-certificates
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/tutorial-aovpn-deploy-create-certificates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 8263c825-c125-89d7-1bd9-1a8c863b6cda
---

# Tutorial: Configure Certificate Authority Templates for Always On VPN | Microsoft Learn

This tutorial shows you how to configure the Certificate Authority (CA) templates for the Always On VPN deployment. It continues the series to deploy Always On VPN in a sample environment. Previously in the series, you [deployed a sample infrastructure](tutorial-aovpn-deploy-setup).

The CA templates are used to issue certificates to the VPN server, NPS server, and users. The certificates are used to authenticate the VPN server and NPS server to clients, and to authenticate users to the VPN server.

In this tutorial, you:

- Create a user authentication template.
- Create a VPN server authentication template.
- Create a NPS server authentication template.
- Enroll and validate the user certificate.
- Enroll and validate the VPN server certificate.
- Enroll and validate the NPS server certificate.

Here's a description of the different templates:

| Template | Description |
| --- | --- |
| **User authentication template** | This template is used to issue user certificates for VPN clients. The user certificate is used to authenticate the user to the VPN server.With a user authentication template, you can improve certificate security by selecting upgraded compatibility levels and choosing the Microsoft Platform Crypto Provider. With the Microsoft Platform Crypto Provider, you can use a [Trusted Platform Module (TPM)](/en-us/windows/device-security/tpm/trusted-platform-module-overview) on client computers to secure the certificate. The user template is configured for autoenrollment. |
| **VPN server authentication template** | This template is used to issue a server certificate for the VPN server. The server certificate is used to authenticate the VPN server to the client.With a VPN server authentication template, you add the IP Security (IPsec) IKE Intermediate application policy. The IP Security (IPsec) IKE Intermediate application policy determines how the certificate can be used, it can allow the server to filter certificates if more than one certificate is available. Because VPN clients access this server from the public internet, the subject and alternative names are different than the internal server name. As a result, you don't configure the VPN server certificate for autoenrollment. |
| **NPS server authentication template** | This template is used to issue a server certificate for the NPS server. The NPS server certificate is used to authenticate the NPS server to the VPN server.With an NPS server authentication template, you copy the standard RAS and IAS Servers template, and scope it for your NPS server. The new NPS server template includes the server authentication application policy. |

To learn more about Always On VPN, including supported integrations, security and connectivity features, see [Always On VPN Overview](overview-always-on-vpn).

## Prerequisites

To complete the steps in this tutorial, you need:

- To complete all the steps in the previous tutorial: [Deploy Always On VPN Infrastructure](tutorial-aovpn-deploy-setup).
- A Windows client device running a supported version of Windows to connect to Always On VPN that is joined to the Active Directory domain.

## Create the user authentication template

1. On the server with Active Directory Certificate Services installed, which in this tutorial is the domain controller, open the Certification Authority snap-in.
2. In the left pane, right-click **Certificate Templates** and select **Manage**.
3. In the Certificate Templates console, right-click **User** and select **Duplicate Template**. Don't select **Apply** or **OK** until you finish entering information for all tabs. Some choices can only be configured at template creation; if you select these buttons before entering all parameters you can't change them, otherwise you need to delete the template and recreate it.
4. In the Properties of **New Template** dialog box, on the **General** tab, complete the following steps:

    1. In **Template display name**, enter **VPN User Authentication**.
    2. Clear the **Publish certificate in Active Directory** check box.
5. On the **Security** tab, complete the following steps:

    1. Select **Add**.
    2. On the Select Users, Computers, Service Accounts, or Groups dialog, enter **VPN Users**, then select **OK**.
    3. In **Group or user names**, select **VPN Users**.
    4. In **Permissions for VPN Users**, select the **Enroll** and **Autoenroll** check boxes in the **Allow** column.

        Important

        Make sure to keep the **Read** permission check box selected. You need Read permissions for enrollment.
    5. In **Group or user names**, select **Domain Users**, then select **Remove**.
6. On the **Compatibility** tab, complete the following steps:

    1. In **Certification Authority**, select *Windows Server 2016*.
    2. On the **Resulting changes** dialog, select **OK**.
    3. In **Certificate recipient**, select *Windows 10/Windows Server 2016*.
    4. On the **Resulting changes** dialog, select **OK**.
7. On the **Request Handling** tab, clear **Allow private key to be exported**.
8. On the **Cryptography** tab, complete the following steps:

    1. In **Provider Category**, select **Key Storage Provider**.
    2. Select **Requests must use one of the following providers**.
    3. Select both **Microsoft Platform Crypto Provider** and **Microsoft Software Key Storage Provider**.
9. On the **Subject Name** tab, clear the **Include e-mail name in subject name** and **E-mail name**.
10. Select **OK** to save the VPN User Authentication certificate template.
11. Close the Certificate Templates console.
12. In the left pane of the Certification Authority snap-in, right-click **Certificate Templates**, select **New** and then select **Certificate Template to Issue**.
13. Select **VPN User Authentication**, then select **OK**.

## Create the VPN Server authentication template

1. In the left pane of the Certification Authority snap-in, right-click **Certificate Templates** and select **Manage** to open the Certificate Templates console.
2. In the Certificate Templates console, right-click **RAS and IAS Server** and select **Duplicate Template**. Don't select **Apply** or **OK** until you finish entering information for all tabs. Some choices can only be configured at template creation; if you select these buttons before entering all parameters you can't change them, otherwise you need to delete the template and recreate it.
3. On the Properties of **New Template** dialog box, on the **General** tab, in **Template display name**, enter **VPN Server Authentication**.
4. On the **Extensions** tab, complete the following steps:

    1. Select **Application Policies**, then select **Edit**.
    2. In the **Edit Application Policies Extension** dialog, select **Add**.
    3. On the **Add Application Policy** dialog, select **IP security IKE intermediate**, then select **OK**.
    4. Select **OK** to return to the **Properties of New Template** dialog.
5. On the **Security** tab, complete the following steps:

    1. Select **Add**.
    2. On the **Select Users, Computers, Service Accounts, or Groups** dialog, enter **VPN Servers**, then select **OK**.
    3. In **Group or user names**, select **VPN Servers**.
    4. In **Permissions for VPN Servers**, select **Enroll** in the **Allow** column.
    5. In **Group or user names**, select **RAS and IAS Servers**, then select **Remove**.
6. On the **Subject Name** tab, complete the following steps:

    1. Select **Supply in the Request**.
    2. On the **Certificate Templates** warning dialog box, select **OK**.
7. Select **OK** to save the VPN Server certificate template.
8. Close the Certificate Templates console.
9. In the left pane of the Certificate Authority snap-in, right-click **Certificate Templates**. Select **New** and then select **Certificate Template to Issue**.
10. Select **VPN Server Authentication**, then select **OK**.
11. Restart the VPN server.

## Create the NPS Server authentication template

1. In the left pane of the Certification Authority snap-in, right-click **Certificate Templates** and select **Manage** to open the Certificate Templates console.
2. In the Certificate Templates console, right-click **RAS and IAS Server** and select **Duplicate Template**. Don't select **Apply** or **OK** until you finish entering information for all tabs. Some choices can only be configured at template creation; if you select these buttons before entering all parameters you can't change them, otherwise you need to delete the template and recreate it.
3. On the Properties of New Template dialog box, on the **General** tab, in **Template display name**, enter *NPS Server Authentication*.
4. On the **Security** tab, complete the following steps:

    1. Select **Add**.
    2. On the **Select Users, Computers, Service Accounts, or Groups** dialog, enter **NPS Servers**, then select **OK**.
    3. In **Group or user names**, select **NPS Servers**.
    4. In **Permissions for NPS Servers**, select **Enroll** in the **Allow** column.
    5. In **Group or user names**, select **RAS and IAS Servers**, then select **Remove**.
5. Select **OK** to save the NPS Server certificate template.
6. Close the Certificate Templates console.
7. In the left pane of the Certificate Authority snap-in, right-click **Certificate Templates**. Select **New** and then select **Certificate Template to Issue**.
8. Select **NPS Server Authentication**, then select **OK**.

Now you created the certificate templates you need to enroll and validate the certificates.

## Enroll and validate the user certificate

Group Policy is configured to autoenroll user certificates, so once the policy is applied to Windows client devices, they automatically enroll the user account for the correct certificate. You can then validate the certificate in the **Certificates** console on the local device.

To check the policy is applied and the certificate is enrolled:

1. Sign in to the Windows client device as the user that you created for the **VPN Users** group.
2. Open Command Prompt and run the following command. Alternatively, restart the Windows client device.

    ```cmd
    gpupdate /force
    ```
3. On the Start menu, type **certmgr.msc**, and press ENTER.
4. In the Certificates snap-in, under **Personal**, select **Certificates**. Your certificates appear in the details pane.
5. Right-click the certificate that has your current domain username, and then select **Open**.
6. On the **General** tab, confirm that the date listed under **Valid from** is today's date. If it isn't, you might have selected the wrong certificate.
7. Select **OK**, and close the Certificates snap-in.

## Enroll and validate the VPN server certificate

To enroll the VPN server's certificate:

1. On the VPN server's Start menu, type **certlm.msc** to open the Certificates snap-in, and press ENTER.
2. Right-click **Personal**, select **All Tasks** and then select **Request New Certificate** to start the Certificate Enrollment Wizard.
3. On the Before You Begin page, select **Next**.
4. On the Select Certificate Enrollment Policy page, select **Next**.
5. On the Request Certificates page, select **VPN Server Authentication**.
6. Under the VPN server check box, select **More information is required** to open the Certificate Properties dialog box.
7. Select the **Subject** tab and enter the following information in the **Subject name** section:

    1. For **Type** select *Common Name*.
    2. For **Value**, enter the name of the external domain that clients use to connect to the VPN (for example, vpn.contoso.com).
    3. Select **Add**.
8. Select **OK** to close Certificate Properties.
9. Select **Enroll**.
10. Select **Finish**.

To validate the VPN server certificate:

1. In the Certificates snap-in, under **Personal**, select **Certificates**. Your listed certificates should appear in the details pane.
2. Right-click the certificate that has your VPN server's name, and then select **Open**.
3. On the **General** tab, confirm that the date listed under **Valid from** is today's date. If it isn't, you might have selected the wrong certificate.
4. On the **Details** tab, select **Enhanced Key Usage**, and verify that **IP security IKE intermediate** and **Server Authentication** display in the list.
5. Select **OK** to close the certificate.

## Enroll and validate the NPS certificate

To enroll the NPS certificate:

1. On the NPS server's Start menu, type **certlm.msc** to open the Certificates snap-in, and press ENTER.
2. Right-click **Personal**, select **All Tasks** and then select **Request New Certificate** to start the Certificate Enrollment Wizard.
3. On the Before You Begin page, select **Next**.
4. On the Select Certificate Enrollment Policy page, select **Next**.
5. On the Request Certificates page, select **NPS Server Authentication**.
6. Select **Enroll**.
7. Select **Finish**.

To validate the NPS certificate:

1. In the Certificates snap-in, under **Personal**, select **Certificates**. Your listed certificates should appear in the details pane.
2. Right-click the certificate that has your NPS server's name, and then select **Open**.
3. On the **General** tab, confirm that the date listed under **Valid from** is today's date. If it isn't, you might have selected the wrong certificate.
4. Select **OK**, and close the Certificates snap-in.