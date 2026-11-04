---
layout: Conceptual
title: Install Windows Admin Center | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/deploy/install
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn how to install Windows Admin Center on a Windows PC or on a server so that multiple users can access Windows Admin Center by using a web browser.
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-28T00:00:00.0000000Z
locale: en-us
document_id: 49b4fd75-78b8-2a23-f908-9b048f04d831
document_version_independent_id: ff42b689-4845-e9f0-d124-292b614fd016
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/deploy/install.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/deploy/install
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/deploy/install.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: a6f13835-b451-ae29-89de-25ffd8d3ea5e
---

# Install Windows Admin Center | Microsoft Learn

This article explains how to install Windows Admin Center on a Windows PC or a Windows Server remote server so that multiple users can use Windows Admin Center in a web browser.

Tip

New to Windows Admin Center? Learn more about [Windows Admin Center](../overview) or [download now](https://www.microsoft.com/evalcenter/download-windows-admin-center).

## Determine your installation type

Review the [installation options](../plan/installation-options), which include the [supported operating systems](../plan/installation-options#installation-supported-operating-systems). To install Windows Admin Center on a virtual machine (VM) in Azure, see [Deploy Windows Admin Center in Azure](../azure/deploy-wac-in-azure).

## Download the Windows Admin Center installer

Download the Windows Admin Center installer from the [Windows Admin Center Evaluation Center](https://www.microsoft.com/evalcenter/download-windows-admin-center) to a location on the machine where you want to install Windows Admin Center.

## Prerequisites

- A Windows PC or server on which to install Windows Admin Center.
- Admin privileges or equivalent permissions on the machine on which you're installing Windows Admin Center.
- Optional: A TLS/SSL certificate for *Server Authentication (1.3.6.1.5.5.7.3.1)*. Use a self-signed certificate for testing, but always use a certificate from a trusted certificate authority for production environments. If you don't have a certificate, use the Windows Admin Center installer to generate a self-signed certificate. The certificate is valid for 60 days.

## Install Windows Admin Center

To install Windows Admin Center, follow the steps for the desktop experience or Windows Server Core.

# [Desktop experience](#tab/desktop-experience)
To install Windows Admin Center on your machine running the Windows Server desktop experience, follow these steps:

1. Sign in to the machine where you want to install Windows Admin Center.
2. Run the Windows Admin Center installer that you previously downloaded.

    ![Screenshot that shows the Windows Admin Center v2 installer setup wizard welcome page.](../media/windows-admin-center-v2-installer.png)
3. On the **Welcome to the Windows Admin Center setup wizard** page, select **Next**.
4. On the **License Terms and Privacy Statement** page, if you agree to the terms, select **I accept these terms and understand the privacy statement**. Then select **Next** to prepare your environment and start the installation process.

    ![Screenshot that shows the Windows Admin Center v2 installer with two installation modes for express or custom setup.](../media/windows-admin-center-v2-installation-mode.png)
5. On the **Select installation mode** page, select either **Express setup** or **Custom setup**:

    - **Express setup**: Determines your network access and port selection based on your operating system. Express setup doesn't allow for configuration of extra features.
    - **Custom setup**: Allows you to configure network access, port numbers, Transport Layer Security (TLS) certificate type and thumbprint, fully qualified domain name of the endpoint, trusted hosts mode, and WinRM over HTTPS.
6. Select **Next**.
7. On the **Select TLS certificate** page, select the option that matches your needs, and then select **Next**.

    You must select which TLS certificate that Windows Admin Center should use. If you already have a certificate, it must be installed in the `LocalMachine\My` certificates store. If you install Windows Admin Center for testing purposes only, the installer can generate a self-signed certificate that expires after 60 days.

    ![Screenshot that shows the Windows Admin Center v2 installer with the certificate options.](../media/select-tls-certificate.png)
8. On the **Automatic updates** page, select your preferred update option. The recommended option to install updates automatically is selected by default. Then select **Next**.
9. On the **Send diagnostic data to Microsoft** page, select your preference, and then select **Next**.
10. Review **Ready to install**, and then select **Install** to start the installation process.
11. After the installation process finishes, select **Start Windows Admin Center** checkbox, and then select **Finish**.
12. Sign in as an administrator to start using Windows Admin Center.

    ![Screenshot that shows the Windows Admin Center sign-in page in the browser window.](../media/sign-in-to-windows-admin-center.png)

# [Server Core](#tab/server-core)
To install Windows Admin Center on a machine running the Windows Server Core experience or by using Windows PowerShell, follow these steps:

1. Sign in to your machine. If you're on Server Core, from the `SConfig` menu, enter option **15**, and then select Enter to open a PowerShell session. If you're on the desktop experience, remote desktop into your VM and start PowerShell.
2. Download the Windows Admin Center installer, and copy it to your computer by using the following PowerShell command:

    ```powershell
    $parameters = @{
         Source = "https://aka.ms/WACdownload"
         Destination = ".\WindowsAdminCenter.exe"
    }
    Start-BitsTransfer @parameters
    ```
3. To install Windows Admin Center, run the following command:

    ```powershell
    Start-Process -FilePath '.\WindowsAdminCenter.exe' -ArgumentList '/VERYSILENT' -Wait
    ```
4. You might also need to start Windows Admin Center by using the following command:

    ```powershell
    Start-Service -Name WindowsAdminCenter
    ```

Tip

You can use the following options for the `-ArgumentList` parameter:

- /Silent
- /VerySilent
- /HTTPSPortNumber
- /CertificateThumbprint

To specify the HTTPS port number and certificate thumbprint on installation through PowerShell, run the following command:

```powershell
.\WindowsAdminCenter2511.exe /HTTPSPortNumber=1234 /CertificateThumbprint=“1234abcd4567efgh”
```

---