---
layout: Conceptual
title: Configure Certificate Auto-Enrollment for Network Policy Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/server-certs/configure-server-certificate-auto-enrollment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to configure server and user certificate auto-enrollment for NPS using Group Policy. Ensure secure, automated certificate management.
ms.topic: how-to
ai-usage: ai-assisted
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-30T00:00:00.0000000Z
locale: en-us
document_id: 78441b98-1d48-8726-226c-31f4558ba513
document_version_independent_id: 7aa9daf3-cbf0-db33-5aab-9c948197ca71
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/server-certs/configure-server-certificate-auto-enrollment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/server-certs/configure-server-certificate-auto-enrollment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/server-certs/configure-server-certificate-auto-enrollment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7e6f3f1d-de32-a14b-a6cc-13d2601a3ba2
---

# Configure Certificate Auto-Enrollment for Network Policy Server | Microsoft Learn

Certificate auto-enrollment simplifies the process of deploying and managing certificates to servers that are running Network Policy Server (NPS) in an Active Directory environment. This article describes how to configure auto-enrollment for both server and user certificates using Group Policy. By following these steps, you can help ensure that certificates are automatically issued, renewed, and managed for your organization's servers and users.

## Prerequisites

Before you begin, ensure the following prerequisites are met:

- Active Directory Certificate Services (AD CS) is installed and configured with at least one Enterprise Certification Authority (CA).
- You configured the server certificate template for auto-enrollment. For more information, see [Configure a server certificate template for auto-enrollment](configure-the-server-certificate-template).
- You have a use account that is a member of both the **Enterprise Admins** and the root domain's **Domain Admins** security groups.
- Access to the following management consoles:

    - Group Policy Management.
    - Network Policy Server.

## Configure server and user certificate auto-enrollment

To configure auto-enrollment for server certificates, follow these steps:

1. Open the Group Policy Management console.
2. Expand the nodes for your Active Directory forest and domain and locate the **Default Domain Policy**. Right-click the **Default Domain Policy** and select **Edit**, which opens the Group Policy Management Editor.
3. Navigate to the following path in the Group Policy Management Editor: **Computer Configuration** &gt; **Policies** &gt; **Windows Settings** &gt; **Security Settings** &gt; **Public Key Policies**.
4. In the details pane, double-click **Certificate Services Client - Auto-Enrollment**. The **Properties** dialog box opens. Configure the following items:

    1. For **Configuration Model**, select **Enabled**.
    2. Check the box for **Renew expired certificates, update pending certificates, and remove revoked certificates**.
    3. Check the box for **Update certificates that use certificate templates**.
5. Select **OK**. Keep the Group Policy Management Editor console open to configure user certificate auto-enrollment.
6. Navigate to the following path: **User Configuration** &gt; **Policies** &gt; **Windows Settings** &gt; **Security Settings** &gt; **Public Key Policies**.
7. In the details pane, double-click **Certificate Services Client - Auto-Enrollment**. The **Properties** dialog box opens. Configure the following items:

    1. For **Configuration Model**, select **Enabled**.
    2. Check the box for **Renew expired certificates, update pending certificates, and remove revoked certificates**.
    3. Check the box for **Update certificates that use certificate templates**.
8. Select **OK**, then close the Group Policy Management Editor console.
9. Refresh the Group Policy settings on your NPS servers to apply the auto-enrollment settings. You can force an immediate refresh by running the following command in an elevated Command Prompt:

    ```cmd
    gpupdate /force
    ```

## Verify server certificate enrollment for NPS

Once you configure auto-enrollment and refreshed Group Policy, you can verify that the server certificate is enrolled successfully. To verify that a server certificate is correctly configured and is enrolled to the NPS, you create a test network policy and allow NPS to verify that NPS can use the certificate for authentication. You don't complete the wizard, so the test network policy isn't created in NPS, but you can verify that the server certificate is enrolled.

To verify NPS enrollment of a server certificate:

1. Open the **Network Policy Server** console.
2. Expand **Policies** and select **Network Policies**.
3. Right-click **Network Policies**, then select **New**. The **New Network Policy** wizard opens.
4. For **Specify Network Policy Name and Connection Type**, in **Policy name**, enter a name, such as *Test auto-enrollment policy*. Ensure that **Type of network access server** has the value **Unspecified**, then select **Next**.
5. For **Specify Conditions**, select **Add**. Select **Windows Groups**, then select **Add**.
6. For **Windows Groups**, select **Add Groups**. Enter a valid group, such as **Domain Users**, then select **OK**. Select **OK** again for **Windows Groups**. Verify your group is listed as a condition, then select **Next**.
7. For **Specify Access Permission**, ensure that **Access granted** is selected, then select **Next**.
8. For **Configure Authentication Methods**, select **Add**. For **Add EAP**, select **Microsoft: Protected EAP (PEAP)**, then select **OK**.
9. In **EAP Types**, select **Microsoft: Protected EAP (PEAP)**, then select **Edit**.
10. In the **Edit Protected EAP Properties** dialog box, in **Certificate issued to**, NPS displays the name of your server certificate as a fully qualified domain name (FQDN). For example, if your NPS is named NPS-01 and your domain is example.com, NPS displays the certificate **NPS-01.example.com**. In addition, in **Issuer**, the name of your certification authority is displayed, and in **Expiration date**, the date of expiration of the server certificate is shown.

    Important

    If NPS doesn't display a valid server certificate and if it provides the message that such a certificate can't be found on the local computer, there are two possible reasons:

    1. Group Policy didn't refresh properly, and the NPS server didn't enroll a certificate from the CA. In this circumstance, restart the NPS server. When the server restarts, Group Policy is refreshed, and you can try again to verify that the server certificate is enrolled.
    2. Either the certificate template, certificate auto-enrollment, or both aren't configured correctly. To resolve these issues, verify you followed all the steps in this article correctly to ensure that the settings that you provided are accurate.
11. Once you verify the presence of a valid server certificate, you can select **OK** and **Cancel** to exit the wizard. Because you aren't completing the wizard, the test network policy isn't created in NPS.

This process demonstrates that your NPS enrolled a valid server certificate that it can use to prove its identity to client computers that are trying to access the network through your network access servers, such as virtual private network (VPN) servers, 802.1X-capable wireless access points, Remote Desktop Gateway servers, and 802.1X-capable Ethernet switches.