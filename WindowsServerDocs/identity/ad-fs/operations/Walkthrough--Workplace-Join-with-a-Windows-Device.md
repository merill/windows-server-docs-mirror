---
layout: Conceptual
title: Walkthrough - Workplace Join with a Windows Device | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/walkthrough--workplace-join-with-a-windows-device
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Walkthrough: Workplace Join with a Windows Device'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 2f124f34-1b8c-ebe6-ea8a-b57a4ed74792
document_version_independent_id: 6f414f8d-a256-d50b-f8c2-d1566483ae2d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Walkthrough--Workplace-Join-with-a-Windows-Device.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/walkthrough--workplace-join-with-a-windows-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Walkthrough--Workplace-Join-with-a-Windows-Device.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 3633ac59-0b48-00a6-7aa7-33c5add636ff
---

# Walkthrough - Workplace Join with a Windows Device | Microsoft Learn

This topic demonstrates how to use Workplace Join to connect your Windows device with your workplace and how to access a web application by using Single Sign-On. You must complete the steps in the [Set up the lab environment for AD FS in Windows Server 2012 R2](../deployment/set-up-the-lab-environment-for-ad-fs-in-windows-server-2012-r2) section before you can try out this walkthrough.

## Access the web application before device registration

In this walkthrough, you access a company web application before you join your device to the workplace. The webpage displays the claims that were included in your security token. Notice that the list of claims does not include any information about your device. You might also observe that you do not have Single Sign-On.

#### To access the web application before you use Workplace Join on your device

1. Log on to Client1 with your Microsoft account.
2. Open Internet Explorer and browse to your generic claims app, **`https://webserv1.contoso.com/claimapp`**.
3. Log on to the webpage by using a company domain account: **roberth@contoso.com**, password: **P@ssword**.
4. The webpage lists all the claims in your security token. Only user claims are present in your security token.
5. Close Internet Explorer.
6. Open Internet Explorer and navigate to the same claims app, **`https://webserv1.contoso.com/claimapp`**.
7. Notice that you are prompted to enter your credentials again. You are not connected to the workplace from a device with Workplace Join and therefore do not have Single Sign-On.

## Join your device with Workplace Join

Important

For Workplace Join to succeed, the client computer (Client1) must trust the SSL certificate that was used to configure Active Directory Federation Services (AD FS) in [Step 2: Configure the Federation Server with Device Registration Service (ADFS1)](../deployment/set-up-the-lab-environment-for-ad-fs-in-windows-server-2012-r2#BKMK_4). It must also be able to validate revocation information for the certificate. If you have any issues with Workplace Join, you can view the event log on Client1.

To see the event log, open Event Viewer, expand **Applications and Services Logs**, expand **Microsoft**, expand **Windows**, and then click **Workplace Join**.

#### To join your device with Workplace Join

1. Log on to Client1 with your Microsoft account.
2. On the **Start** screen, open the **Charms** bar, and then select the **Settings** charm. Select **Change PC Settings**.
3. On the **PC Settings** page, select **Network**, and then click **Workplace**.
4. In the **Enter your UserID to get workplace access or turn on device management** box, type **roberth@contoso.com**, and then click **Join**.
5. When you are prompted for credentials, type **roberth@contoso.com**, and password: **P@ssword**. Click **OK**.
6. You should now see the message: "This device has joined your workplace network."

### Access the web application after joining the workplace

In this part of the demonstration, you access a company web application from your device that is connected with Workplace Join. The webpage displays the claims that were included in your security token. Notice that the list of claims includes both device and user information. You might also observe that you now have Single Sign-On.

##### To access the web application after joining the workplace

1. Log on to **Client1** with your Microsoft account.
2. Open Internet Explorer and browse to your generic claims app, **`https://webserv1.contoso.com/claimapp`**.
3. Log on to the webpage by using a company domain account: **roberth@contoso.com**, password: **P@ssword**.
4. The webpage lists claims in your security token. Your token contains both user and device claims.
5. Close Internet Explorer.
6. Open Internet Explorer and navigate to the same claims app, **`https://webserv1.contoso.com/claimapp`**.
7. Notice that you are **not** prompted to enter your credentials again. You are connected from a device with Workplace Join and therefore have Single Sign-On.