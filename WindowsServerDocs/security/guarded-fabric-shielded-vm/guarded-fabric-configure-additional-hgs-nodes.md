---
layout: Conceptual
title: Configure additional HGS nodes | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configure-additional-hgs-nodes
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Configure additional HGS nodes'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2020-01-14T00:00:00.0000000Z
locale: en-us
document_id: 8f8b7519-7a6f-b4fd-b510-392f027a6540
document_version_independent_id: e2dda892-19eb-54eb-07e0-7de152349d85
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configure-additional-hgs-nodes.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-configure-additional-hgs-nodes
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configure-additional-hgs-nodes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7c01134-b8f3-438c-822d-13471e513908
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/82fff6b2-939d-4e9a-8f9c-d1c41a59749b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1e467277-61ac-ee64-ef97-b6206b0dfdd4
---

# Configure additional HGS nodes | Microsoft Learn

In production environments, HGS should be set up in a high availability cluster to ensure that shielded VMs can be powered on even if an HGS node goes down. For test environments, secondary HGS nodes are not required.

Use one of these methods to add HGS nodes, as best suited for your environment.

| Environment | Option 1 | Option 2 |
| --- | --- | --- |
| New HGS forest | Using PFX files | Using certificate thumbprints |
| Existing bastion forest | Using PFX files | Using certificate thumbprints |

## Prerequisites

Make sure that each additional node:

- Has the same hardware and software configuration as the primary node
- Is connected to the same network as the other HGS servers
- Can resolve the other HGS servers by their DNS names

## Dedicated HGS forest with PFX certificates

1. Promote the HGS node to a domain controller
2. Initialize the HGS server

### Promote the HGS node to a domain controller

1. Run [Install-HgsServer](https://technet.microsoft.com/itpro/powershell/windows/hgsserver/install-hgsserver) to join the domain and promote the node to a domain controller.

    ```powershell
    $adSafeModePassword = ConvertTo-SecureString -AsPlainText '<password>' -Force
    
    $cred = Get-Credential 'relecloud\Administrator'
    
    Install-HgsServer -HgsDomainName 'bastion.local' -HgsDomainCredential $cred -SafeModeAdministratorPassword $adSafeModePassword -Restart
    ```
2. When the server reboots, log in with a domain administrator account.

### Initialize the HGS server

Run the following command to join the existing HGS cluster.

```powershell
Initialize-HgsServer -HgsServerIPAddress <IP address of first HGS Server>
```

## Dedicated HGS forest with certificate thumbprints

1. Promote the HGS node to a domain controller
2. Initialize the HGS server
3. Install the private keys for the certificates

### Promote the HGS node to a domain controller

1. Run [Install-HgsServer](https://technet.microsoft.com/itpro/powershell/windows/hgsserver/install-hgsserver) to join the domain and promote the node to a domain controller.

    ```powershell
    $adSafeModePassword = ConvertTo-SecureString -AsPlainText '<password>' -Force
    
    $cred = Get-Credential 'relecloud\Administrator'
    
    Install-HgsServer -HgsDomainName 'bastion.local' -HgsDomainCredential $cred -SafeModeAdministratorPassword $adSafeModePassword -Restart
    ```
2. When the server reboots, log in with a domain administrator account.

### Initialize the HGS server

Run the following command to join the existing HGS cluster.

```powershell
Initialize-HgsServer -HgsServerIPAddress <IP address of first HGS Server>
```

### Install the private keys for the certificates

If you did not provide a PFX file for either the encryption or signing certificates on the first HGS server, only the public key will be replicated to this server. You will need to install the private key by importing a PFX file containing the private key into the local certificate store or, in the case of HSM-backed keys, configuring the Key Storage Provider and associating it with your certificates per your HSM manufacturer's instructions.

## Existing bastion forest with PFX certificates

1. Join the node to the existing domain
2. Grant the machine rights to retrieve gMSA password and run Install-ADServiceAccount
3. Initialize the HGS server

### Join the node to the existing domain

1. Ensure at least one NIC on the node is configured to use the DNS server on your first HGS server.
2. Join the new HGS node to the same domain as your first HGS node.

### Grant the machine rights to retrieve gMSA password and run Install-ADServiceAccount

1. Have a directory services admin add the computer account for your new node to the security group containing all of your HGS servers that is permissioned to allow those servers to use the HGS gMSA account.
2. Reboot the new node to obtain a new Kerberos ticket that includes the computer's membership in that security group. After the reboot completes, sign in with a domain identity that belongs to the local administrators group on the computer.
3. Install the HGS group managed service account on the node.

    ```powershell
    Install-ADServiceAccount -Identity <HGSgMSAAccount>
    ```

### Initialize the HGS server

Run the following command to join the existing HGS cluster.

```powershell
Initialize-HgsServer -HgsServerIPAddress <IP address of first HGS Server>
```

## Existing bastion forest with certificate thumbprints

1. Join the node to the existing domain
2. Grant the machine rights to retrieve gMSA password and run Install-ADServiceAccount
3. Initialize the HGS server
4. Install the private keys for the certificates

### Join the node to the existing domain

1. Ensure at least one NIC on the node is configured to use the DNS server on your first HGS server.
2. Join the new HGS node to the same domain as your first HGS node.

### Grant the machine rights to retrieve gMSA password and run Install-ADServiceAccount

1. Have a directory services admin add the computer account for your new node to the security group containing all of your HGS servers that is permissioned to allow those servers to use the HGS gMSA account.
2. Reboot the new node to obtain a new Kerberos ticket that includes the computer's membership in that security group. After the reboot completes, sign in with a domain identity that belongs to the local administrators group on the computer.
3. Install the HGS group managed service account on the node.

    ```powershell
    Install-ADServiceAccount -Identity <HGSgMSAAccount>
    ```

### Initialize the HGS server

Run the following command to join the existing HGS cluster.

```powershell
Initialize-HgsServer -HgsServerIPAddress <IP address of first HGS Server>
```

It will take up to 10 minutes for the encryption and signing certificates from the first HGS server to replicate to this node.

### Install the private keys for the certificates

If you did not provide a PFX file for either the encryption or signing certificates on the first HGS server, only the public key will be replicated to this server. You will need to install the private key by importing a PFX file containing the private key into the local certificate store or, in the case of HSM-backed keys, configuring the Key Storage Provider and associating it with your certificates per your HSM manufacturer's instructions.

## Configure HGS for HTTPS communications

If you want to secure HGS endpoints with an SSL certificate, you must configure the SSL certificate on this node, as well as every other node in the HGS cluster. SSL certificates *are not* replicated by HGS and do not need to use the same keys for every node (i.e. you can have different SSL certs for each node).

When requesting an SSL cert, ensure the cluster fully qualified domain name (as shown in the output of `Get-HgsServer`) is either the subject common name of the cert, or included as a subject alternative DNS name. When you've obtained a certificate from your certificate authority, you can configure HGS to use it with [Set-HgsServer](/en-us/powershell/module/hgsserver/set-hgsserver).

```powershell
$sslPassword = Read-Host -AsSecureString -Prompt "SSL Certificate Password"
Set-HgsServer -Http -Https -HttpsCertificatePath 'C:\temp\HgsSSLCertificate.pfx' -HttpsCertificatePassword $sslPassword
```

If you already installed the certificate into the local certificate store and want to reference it by thumbprint, run the following command instead:

```powershell
Set-HgsServer -Http -Https -HttpsCertificateThumbprint 'A1B2C3D4E5F6...'
```

HGS will always expose both the HTTP and HTTPS ports for communication. It is unsupported to remove the HTTP binding in IIS, however you can use the Windows Firewall or other network firewall technologies to block communications over port 80.

## Decommission an HGS node

To decommission an HGS node:

1. [Clear the HGS configuration](guarded-fabric-manage-hgs#clearing-the-hgs-configuration).

    This removes the node from the cluster and uninstalls the attestation and key protection services. If it's the last node in the cluster, -Force is needed to signify you do want to remove the last node and destroy the cluster in Active Directory.

    If HGS is deployed in a bastion forest (default), that's the only step. You can optionally unjoin the machine from the domain and remove the gMSA account from Active Directory.
2. If HGS created its own domain, you should also [uninstall HGS](guarded-fabric-manage-hgs#clearing-the-hgs-configuration) to unjoin the domain and demote the domain controller.