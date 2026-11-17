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
description: Install Windows Admin Center in Administration Mode or Virtualization Mode with the combined installer, and configure TLS, updates, and settings for signing in.
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2026-10-08T00:00:00.0000000Z
ai-usage: ai-assisted
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

Windows Admin Center is a browser-based tool for managing Windows servers and clusters. Its combined installer supports Administration Mode and Virtualization Mode. Choose the mode that matches whether you need general server administration or stateful virtualization management at scale.

This article explains how to choose a mode and install Windows Admin Center by using the interactive installer or the command line, with an optional configuration file. Both installation methods support Administration Mode and Virtualization Mode. You then verify the installation and sign in for the first time.

Tip

New to Windows Admin Center? Learn more about [Windows Admin Center](../overview) or [download Windows Admin Center](https://www.microsoft.com/evalcenter/download-windows-admin-center).

## Prerequisites

- A machine that meets the [supported operating system requirements](../plan/installation-options#installation-supported-operating-systems). To install Windows Admin Center on an Azure virtual machine (VM), see [Deploy Windows Admin Center in Azure](../azure/deploy-wac-in-azure).
- Admin privileges or equivalent permissions on the machine where you're installing Windows Admin Center.
- Download the Windows Admin Center installer from the [Windows Admin Center Evaluation Center](https://www.microsoft.com/evalcenter/download-windows-admin-center) to the machine where you want to install Windows Admin Center.
- For Virtualization Mode, a dedicated Windows Server machine with:
    - At least four processor cores.
    - At least 8 GB of memory.
    - At least 10 GB of available disk space.
    - The [Microsoft Visual C++ Redistributable](/en-us/cpp/windows/latest-supported-vc-redist). If it isn't installed, install it manually or allow the installer to download and install it by using `winget`.
- Optional: A Transport Layer Security (TLS) certificate for Server Authentication (`1.3.6.1.5.5.7.3.1`). For production environments, use a certificate from a trusted certification authority that you install in the `LocalMachine\My` certificate store. For testing, the installer can generate a self-signed certificate that expires after 60 days.

## Choose a Windows Admin Center mode

The installer provides the following modes:

- **Administration Mode**: Provides a stateless gateway for general Windows Server administration. This mode doesn't use a database.
- **Virtualization Mode**: Provides a stateful gateway for managing Hyper-V, clusters, and storage at scale. This mode includes a self-managed PostgreSQL database. Install this mode on a dedicated Windows Server machine.

You can't change the mode after installation. To change modes, reinstall Windows Admin Center.

## Install Windows Admin Center

Choose the interactive installer or command line. Both methods support Administration Mode and Virtualization Mode.

# [Interactive installer](#tab/interactive-installer)
To install Windows Admin Center by using the interactive installer:

1. Sign in to the machine where you want to install Windows Admin Center.
2. Run the Windows Admin Center installer.

    ![Screenshot of the Windows Admin Center v2 Installer welcome page with Next and Cancel buttons.](../media/windows-admin-center-v2-installer.png)
3. On the **Welcome to the Windows Admin Center setup wizard** page, select **Next**.
4. On the **License Terms and Privacy Statement** page, if you agree to the terms, select **I accept these terms and understand the privacy statement**, and then select **Next**.
5. On the **Choose your Windows Admin Center mode** page, select **Administration Mode** or **Virtualization Mode**, and then select **Next**.

    ![Screenshot of the Windows Admin Center v2 Installer mode selection page with neither mode selected.](../media/windows-admin-center-v2-mode.png)

 The \*\*Administration Mode\*\* option describes a stateless gateway for general Windows Server administration. It supports about 10 managed nodes and one concurrent connection per gateway. The \*\*Virtualization Mode\*\* option describes a stateful gateway for Hyper-V, clustering, and storage at scale. It includes PostgreSQL, supports up to 1,000 managed nodes, and requires a dedicated Windows Server operating system. Until you select a mode, \*\*Next\*\* is unavailable.
6. If you selected **Virtualization Mode**, review the checks on the **Virtualization Mode Requirements** page. Resolve each unmet requirement:

    - If the Microsoft Visual C++ Redistributable is missing, select **Install automatically using winget (recommended)**, and then select **Install**.
    - To install the redistributable yourself, select **I will install it manually**, use the provided download link to install it, and then refresh the requirement status.

    Continue when the overall status confirms that you meet all requirements.
7. On the **Select installation mode** page, select an installer setup type:

    - **Express setup**: Determines network access and port selection based on the operating system. You can't configure extra features.
    - **Custom setup**: Use this option to configure network access, port numbers, the Transport Layer Security (TLS) certificate type and thumbprint, the fully qualified domain name (FQDN) of the endpoint, trusted hosts mode, and Windows Remote Management (WinRM) over HTTPS.

    Select **Next**.

    ![Screenshot of the Windows Admin Center v2 Installer installation mode page with Express setup selected and Custom setup available.](../media/windows-admin-center-v2-installation-mode.png)
8. On the **Select TLS certificate** page, select one of the following options, and then select **Next**:

    - **Use the pre-installed TLS certificate**: Use a certificate in the `LocalMachine\My` certificate store.
    - **Generate a self-signed certificate (expires in 60 days)**: Use this option for testing only.

    ![Screenshot of the Windows Admin Center v2 Installer TLS certificate page with the self-signed certificate option selected.](../media/select-tls-certificate.png)
9. If you selected **Virtualization Mode**, on the **PostgreSQL Configuration** page, enter the database username, password, password confirmation, and port. Then select **Next**.

    Important

    The PostgreSQL username defaults to `postgres` and the port defaults to `5432`. The username must start with a letter or underscore, contain only letters, digits, and underscores, not start with `pg_`, and contain no more than 63 characters. The decrypted password must contain only printable ASCII characters and can't contain spaces, semicolons, or quotation marks. Use a strong, unique password and store it securely.
10. On the **Automatic updates** page, select your preferred update option. By default, the installer selects the recommended option to install updates automatically. Then select **Next**.
11. On the **Send diagnostic data to Microsoft** page, select your preference, and then select **Next**.
12. On the **Ready to Install** page, review the selected configuration, including the installation mode, port numbers, TLS certificate choice, and FQDN. Then select **Install**.
13. Wait for the installer to finish configuring Windows Admin Center.

# [Command Line](#tab/command-line)
Use the command line to install Administration Mode or Virtualization Mode on Desktop Experience or Server Core:

`/Mode=` overrides the configuration-file `Mode` key. When you omit the mode during silent installation, an existing installation keeps its prior mode, and a fresh installation defaults to Administration Mode.

1. Sign in to the machine. In `SConfig`, enter option **15**, and then select Enter to open a PowerShell session. On Desktop Experience, use Remote Desktop to connect to the machine, and then start PowerShell.
2. Download the Windows Admin Center installer by using the following PowerShell command:

    ```powershell
    $parameters = @{
        Source = "https://aka.ms/WACdownload"
        Destination = ".\WindowsAdminCenter.exe"
    }
    Start-BitsTransfer @parameters
    ```
3. Run the installer for the mode that you want to install.

    For Administration Mode, run:

    ```powershell
    .\WindowsAdminCenter.exe /VERYSILENT /Mode=Administration
    ```

    For Virtualization Mode, run:

    ```powershell
    .\WindowsAdminCenter.exe /VERYSILENT /Mode=Virtualization
    ```

    Use the `/Silent`, `/VerySilent`, `/HTTPSPortNumber`, and `/CertificateThumbprint` installer options to customize the installation. For example:

    ```powershell
    .\WindowsAdminCenter.exe /HTTPSPortNumber=1234 `
        /CertificateThumbprint="AA11BB22CC33DD44EE55FF66AA77BB88CC99DD00"
    ```
4. If necessary, start Windows Admin Center by using the following command:

    ```powershell
    Start-Service -Name WindowsAdminCenter
    ```

### Use a configuration file

Use an INI configuration file to install either mode. All keys are optional. The installer uses default values or automatic detection for omitted keys and deletes the configuration file after processing it. Restrict access to the configuration file while it exists because it contains a credential protected by the Data Protection API (DPAPI). If setup doesn't delete the file, delete it manually.

Set `Mode=Administration` or `Mode=Virtualization`. The `PostgreSQLUsername`, `PostgreSQLPassword`, and `PostgreSQLPort` keys apply only to Virtualization Mode. The installer ignores them in Administration Mode. To use a TLS certificate from the `LocalMachine\My` certificate store, specify its thumbprint in the `Thumbprint` key. If you omit `Thumbprint` or leave it empty, the installer generates a self-signed certificate.

Important

The PostgreSQL username defaults to `postgres` and the port defaults to `5432`. The username must start with a letter or underscore, contain only letters, digits, and underscores, not start with `pg_`, and contain no more than 63 characters. The decrypted password must contain only printable ASCII characters and can't contain spaces, semicolons, or quotation marks. Use a strong, unique password and store it securely.

For Virtualization Mode, `PostgreSQLPassword` must contain a DPAPI-encrypted value. Generate the value on the target machine under the user context that runs the installer because DPAPI output is specific to the machine and user. Use the following PowerShell command, and enter the PostgreSQL password when prompted:

```powershell
Read-Host -Prompt "PostgreSQL password" -AsSecureString | ConvertFrom-SecureString
```

The following example configures Virtualization Mode with the default PostgreSQL username and port. Replace `<DPAPI-encrypted-password>` with the output from the preceding command:

```ini
Mode=Virtualization
PostgreSQLUsername=postgres
PostgreSQLPassword=<DPAPI-encrypted-password>
PostgreSQLPort=5432
Thumbprint=
```

Save the configuration file, and then pass its path to the installer:

```powershell
.\WindowsAdminCenter.exe /ConfigFile="C:\path\to\config.ini"
```

---

## Verify the installation

1. Open the Windows Admin Center endpoint URL (`https://<fully-qualified-domain-name>:<port>`) in a browser by using the FQDN and HTTPS port from the installation. When prompted, enter credentials for an administrator account.

    ![Screenshot of the Windows Admin Center page where you enter a username and password and select the Sign In button.](../media/sign-in-to-windows-admin-center.png)
2. Select **Sign In**.
3. Verify that the Windows Admin Center dashboard loads. In Virtualization Mode, the dashboard identifies the mode and shows the **Welcome to Windows Admin Center** dialog.
4. If the **Welcome to Windows Admin Center** dialog appears, dismiss it to view the dashboard.