---
layout: Conceptual
title: Walkthrough - Workplace Join with an iOS Device | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/walkthrough--workplace-join-with-an-ios-device
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Walkthrough: Workplace Join with an iOS Device'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: c321fa45-093f-7f54-caa2-a94f0dc6d651
document_version_independent_id: ae93143d-a141-b635-e87e-197e53030942
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Walkthrough--Workplace-Join-with-an-iOS-Device.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/walkthrough--workplace-join-with-an-ios-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Walkthrough--Workplace-Join-with-an-iOS-Device.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 6a35bcec-0842-fee5-4b20-c948a1621836
---

# Walkthrough - Workplace Join with an iOS Device | Microsoft Learn

Important

This method is relevant for only fully on-prem customers. Hybrid or cloud-only customers must not use this method to register their iOS devices. And this method is not compatible when the on-prem customers decide to move to cloud. The device must be unregistered and registered with the cloud.

This topic demonstrates Workplace Join on an iOS device. You must complete the steps in the [Set up the lab environment for AD FS in Windows Server 2012 R2](../deployment/set-up-the-lab-environment-for-ad-fs-in-windows-server-2012-r2) section before you can try out this walkthrough. You can use the device to access the same company web application that you accessed in [Walkthrough: Workplace Join with a Windows Device](walkthrough--workplace-join-with-a-windows-device).

## Join an iOS device with Workplace Join

Important

When on-premises DRS is configured, the iOS device must trust the Secure Socket Layer (SSL) certificate that was used to configure Active Directory Federation Services (AD FS) in [Step 2: Configure the federation server (ADFS1) with Device Registration Service](../deployment/set-up-the-lab-environment-for-ad-fs-in-windows-server-2012-r2#BKMK_4), for Workplace Join to succeed.

- If the AD FS SSL certificate was issued from a test certification authority (CA), you must install the certification authority certificate on your iOS device.
- If your certification authority certificate is published on a website, you can browse to the website from your iOS device and install the certificate.

In this demonstration, you join the device to the workplace.

#### To join an iOS device to a workplace

1. - **When Microsoft Entra Device Registration service is the configured DRS:** Open Apple Safari and navigate to Microsoft Entra Device Registration service Over-the-Air Profile endpoint for iOS devices, &lt;`https://enterpriseregistration.windows.net/enrollmentserver/otaprofile/<yourdomainname` &gt; Where &lt;`yourdomainname`&gt; is the domain name that you have configured with Microsoft Entra ID. For example, if your domain name is contoso.com, the URL would be: `https://enterpriseregistration.windows.net/enrollmentserver/otaprofile/contoso.com`
    - **When On-premises DRS is the configured DRS**: Open Apple Safari and navigate to the Device Registration Service (DRS) Over-the-Air Profile endpoint for iOS devices, `https://adf1s.contoso.com/enrollmentserver/otaprofile`

    There are many ways to communicate this URL to your users. One recommended way is to publish this URL in a custom application access denied message in AD FS. This is covered in the upcoming section: [Create an application access policy and custom access denied message](/en-us/azure/active-directory/active-directory-device-registration-on-premises-setup#create-an-application-access-policy-and-custom-access-denied-message)
2. Log on to the webpage by using a company domain account: **roberth@contoso.com** and password: **P@ssword**.
3. You are prompted to install a profile. On the **Install Profile** screen, click **Install**.
4. When prompted to confirm installation of the profile, click **Install Now**.
5. If your device requires a PIN to unlock the device, you are prompted to enter your PIN.
6. The profile installation is finished when you see the **Profile Installed** screen. Click **Done**.

    Return to Safari. A message informs you that you can close or leave Safari.

Tip

To view or remove the Workplace Join profile, browse to **Settings**, click **General**, and then click **Profiles** on your iOS device.