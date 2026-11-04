---
layout: Conceptual
title: Use certificates in Remote Desktop Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/remote-desktop-services-certificates
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: How to create and use authentication certificates for Remote Desktop Services.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2025-07-14T00:00:00.0000000Z
locale: en-us
document_id: 01c97c17-ae19-a7ff-c30c-aead7b90c4a0
document_version_independent_id: 01c97c17-ae19-a7ff-c30c-aead7b90c4a0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/remote-desktop-services-certificates.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/remote-desktop-services-certificates
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/remote-desktop-services-certificates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: c1dc9480-69cd-70c1-7347-7fa2980c09ae
---

# Use certificates in Remote Desktop Services | Microsoft Learn

You can use certificates to secure connections to your Remote Desktop Services (RDS) deployment and between RDS server roles. RDS uses Secure Socket Layer (SSL) or Transport Layer Security (TLS) to encrypt connections to the RDS Web, Connection Broker, and Gateway role services.

Certificates prevent man-in-the-middle attacks, where a bad actor intercepts traffic between the Remote Desktop Protocol (RDP) server and client to steal confidential information or deny access to credentials, by verifying that the server sending information to the client is authentic. When this trust relationship is set up, the client considers the connection secure and can accept data going to and from the server.

## Prerequisites

The following are required to use certificates in RDS:

- A computer or computers where the RDS role is configured. To learn more, see [Install or uninstall roles, role services, or features](../../administration/server-manager/install-or-uninstall-roles-role-services-or-features).
- An account with administrator rights or equivalent to one or more RDS servers.
- A server certificate that meets the following requirements:

    - Issued for Server Authentication (EKU 1.3.6.1.5.5.7.3.1).
    - Issued for Enhanced Key Usage (OID 2.5.29.37).
    - Issued for Key Usage (OID 2.5.29.15).
    - Issued by a certificate authority trusted by one or more RDS servers and clients.
    - Issued with an exportable private key.
    - An export of the certificate with the corresponding private key in `.pfx` format. To learn more about exporting the private key, see [Export a certificate with its private key](../../identity/ad-cs/export-certificate-private-key).

Note

If you're using Active Directory Certificate Services (AD CS) to issue certificates, you can also create a certificate template or duplicate the Web Server certificate template. To learn more about creating certificate templates, see [Create a new certificate template](../../identity/ad-cs/manage-certificate-templates#create-a-new-certificate-template).

## Configure Remote Desktop to use certificates

Now that you created your certificates and understand their contents, you must configure Remote Desktop to use those certificates.

To configure Remote Desktop to use specific certificates:

# [GUI](#tab/gui)
1. In **Server Manager**, on the left pane, select **Remote Desktop Services**.
2. On the **Overview** tab, under **Deployment Overview**, select **TASKS**, then select **Edit Deployment Properties**.
3. In the **Configure the deployment** window, select **Certificates**.
4. Choose **Select existing certificate**, select **Browse**, locate your certificate file in `.pfx` format, then select **Open**.
5. In the **Password** field, enter the password for the certificate you created, then select **OK**.
6. Select the **Allow the certificate to be added to the Trusted Root Certification Authorities certificate store on the destination computers** checkbox, then select **OK**.
7. Select **OK** to finalize your deployment.

Note

Even if you have multiple servers in the deployment, Server Manager imports the certificate to all servers. Server Manager places the certificate in the trusted root for each server, then binds the certificate to its respective roles.

# [PowerShell](#tab/powershell)
1. Sign on to a computer with the RDS Remote Server Administration Tools (RSAT) installed and the RD role you wish to configure.
2. Open an elevated PowerShell session.
3. Run the following script for the RD certificate you plan to use for your session where it prompts you for the password and location for the exported certificate. Replace `<PathToPFXFile>` with the full file path including the `.pfx` file.

```powershell
$password = Read-Host -AsSecureString -Prompt "Enter Password"
$parameters = @{
  Role        = "RDWebAccess"
  Password    = $password
  ImportPath  = "PathToPFXFile"
}
Set-RDCertificate @parameters
```

To set the certificate based on a specific **-Role** type, see [Set-RDCertificate](/en-us/powershell/module/rdmgmt/set-rdcertificate).

To view all of the configured RDS certificates, run the following command:

```powershell
Get-RDCertificate
```

---

You might want to use certificates for the RDS Session Host along with the certificates you configured in Server Manager. For more information about RDS Session Host certificates, see [Remote Desktop listener certificate configurations](/en-us/troubleshoot/windows-server/remote/remote-desktop-listener-certificate-configurations).