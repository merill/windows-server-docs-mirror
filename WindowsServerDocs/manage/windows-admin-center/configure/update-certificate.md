---
layout: Conceptual
title: Update the Administration Mode Certificate | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/configure/update-certificate
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn how to update the single gateway HTTPS certificate used by Windows Admin Center Administration Mode with PowerShell or the installer.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2026-09-30T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 1ab1a5b6-2eb4-cf45-7d67-fb0fd4eaa66f
document_version_independent_id: 1ab1a5b6-2eb4-cf45-7d67-fb0fd4eaa66f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/configure/update-certificate.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/configure/update-certificate
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/configure/update-certificate.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 6192236c-b025-6ed9-ef60-003ec8f5d6ec
---

# Update the Administration Mode Certificate | Microsoft Learn

The gateway HTTPS certificate in Windows Admin Center Administration Mode secures communication between the gateway and connected devices by encrypting data and verifying identities. Update the certificate before it expires, if its private key is compromised, or when your organization changes certificate authorities.

This article explains how to replace the certificate by using PowerShell or the Windows Admin Center installer. The procedure applies only to Administration Mode because Virtualization Mode manages its agent and gateway certificates differently.

You might want to update the certificate in Administration Mode if:

- You have a new certificate authority (CA)
- Your existing private key was disclosed
- You need to renew your certificate

To update this certificate, follow the guidance in this article.

Note

If you use Windows Admin Center in Virtualization Mode, see [Manage certificates in Windows Admin Center Virtualization Mode](../manage-virtualization-mode-certificates) instead.

## Prerequisites

To update the certificate that Windows Admin Center uses, you need the following prerequisites:

- A Windows PC or server with Windows Admin Center installed.
- Administrative privileges or equivalent permissions on the machine you're using Windows Admin Center on.
- A TLS certificate that is:

    - Issued for Server Authentication.
    - Issued by a certificate authority trusted by the Windows Admin Center machine and clients.
    - Valid for the fully qualified domain name (FQDN) or IP address used to access Windows Admin Center.
    - Contains the private key.

Note

Self-signed certificates aren't recommended for use with Windows Admin Center in production environments.

## Update the certificate

# [PowerShell](#tab/powershell)
1. Sign in to your machine. If you're on Server Core, from the SConfig menu, enter option **15**, then select Enter to open a PowerShell session. If you're on the desktop experience, remote desktop into your VM and launch PowerShell.
2. Import the Windows Admin Center configuration PowerShell module by using the following command:

    ```powershell
    Import-Module "$env:ProgramFiles\WindowsAdminCenter\PowerShellModules\Microsoft.WindowsAdminCenter.Configuration"
    ```
3. Apply the new certificate by using the subject name of the certificate. Ensure the certificate uses a unique subject name. You can find the subject name in the `LocalMachine\My\` certificate store on your computer.

    ```powershell
    Get-ChildItem -Path Cert:\LocalMachine\My
    ```

    ```powershell
    Set-WACCertificateSubjectName -SubjectName "<subject name>"
    ```

    Alternatively, you can use the SHA1 thumbprint of the certificate by using the **Thumbprint** parameter. You can find the thumbprint in the `LocalMachine\My\` certificate store on your computer.

    ```powershell
    Set-WACCertificateSubjectName -Thumbprint "<thumbprint>"
    ```
4. Update the certificate access control list to grant permissions for the *Network Service* account to access the certificate. Use the following command, replacing `<subject name>` with the subject name of the certificate:

    ```powershell
    Set-WACCertificateAcl -SubjectName "<subject name>"
    ```
5. You must restart the Windows Admin Center service for the changes to take effect. Restart the Windows Admin Center service by using the following command:

    ```powershell
    Restart-Service -Name WindowsAdminCenter
    ```

# [Windows Admin Center](#tab/wac)
1. Open the installer that matches the version of Windows Admin Center currently installed.
2. Advance through the wizard to the **Select TLS certificate** screen.
3. Select the **Use the pre-installed TLS certificate** option, and then select **Next**.

    ![Screenshot of the Windows Admin Center installer with Use the pre-installed TLS certificate selected.](../media/select-pre-installed-certificate.png)
4. Enter the thumbprint of your certificate. Find the thumbprint in the `LocalMachine\My\` certificate store on your computer.

    ![Screenshot of the Windows Admin Center installer with the empty TLS certificate thumbprint dropdown expanded.](../media/select-thumbprint-certificate.png)
5. Complete the wizard and start Windows Admin Center.

---

## Troubleshoot certificate issues

Several tools help you find logs and error messages. The following diagnostic tools are the most useful:

- **Event Viewer**: Use the Event Viewer under the WindowsAdminCenter event log to diagnose any issues related to the TLS certificate registration process. This tool provides detailed logs that can help pinpoint specific errors.
- **Browser errors**: If you set up the Windows Admin Center service properly but the browser indicates an error, verify the TLS certificate configuration and ensure it matches the required setup parameters.
- **Ajax error**: An Ajax error might appear when you attempt to open a connection with an invalid certificate. To avoid this issue, install and validate the certificate correctly.

### Common problems

- **Invalid certificate**

    - A certificate might be invalid. This condition shows as "invalid certificate."
    - Even if you don't see an error on the WindowsAdminCenter event log, the browser could indicate invalid certificate status as an icon at the address bar. You can't use Windows Admin Center if it uses an invalid certificate when communicating with the subprocesses.
    - You shouldn't generate a self-signed certificate because it's a security issue.
- **Mismatched DNS name**

    - The certificate DNS name might be different from the Windows Admin Center DNS name.
    - If you don't resolve this mismatch, Windows Admin Center might not work or return errors.
- **Wrong or inaccurate thumbprint**

    - Check that the thumbprint is present and correctly registered. If the thumbprint doesn't match what Windows Admin Center expects, Windows Admin Center might not detect the certificate.
- **Private key not configured to be accessed by the network service**

    - The HTTPS protocol layer reads the certificate's private key to encrypt the TLS payload when communicating over the HTTPS protocol.
    - Windows Admin Center uses the Network Service account, so Network Service must be able to access the private key. Use the `certlm.msc` tool to select the **All Tasks** menu and open the **Manage Private Keys...** dialog.
    - Ensure `NETWORK SERVICE` can access the private key.
- **Network, policy, and firewall configuration issues**

    - If you restrict TLS communications, the Windows Admin Center gateway might not be able to access the certificate. This issue might stem from a firewall or Group Policy Object (GPO).