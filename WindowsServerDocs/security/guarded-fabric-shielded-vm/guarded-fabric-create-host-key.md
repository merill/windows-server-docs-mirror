---
layout: Conceptual
title: Create a host key and add it to HGS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-create-host-key
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Create a host key and add it to HGS'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 36180368-7d61-18e9-ec83-c460e40d8e43
document_version_independent_id: b26734be-b816-9ab9-f11d-a6ba05c267e6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-create-host-key.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-create-host-key
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-create-host-key.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 06a943b2-8824-e260-3390-5dd3a185f678
---

# Create a host key and add it to HGS | Microsoft Learn

This topic covers how to prepare Hyper-V hosts to become guarded hosts using host key attestation (Key mode). You'll create a host key pair (or use an existing certificate) and add the public half of the key to HGS.

## Create a host key

1. Install Windows Server 2019 on your Hyper-V host machine.
2. Install the Hyper-V and Host Guardian Hyper-V Support features:

    ```powershell
    Install-WindowsFeature Hyper-V, HostGuardian -IncludeManagementTools -Restart
    ```
3. Generate a host key automatically, or select an existing certificate. If you are using a custom certificate, it should have at least a 2048-bit RSA key, Client Authentication EKU, and Digital Signature key usage.

    ```powershell
    Set-HgsClientHostKey
    ```

    Alternatively, you can specify a thumbprint if you want to use your own certificate. This can be useful if you want to share a certificate across multiple machines, or use a certificate bound to a TPM or an HSM. Here's an example of creating a TPM-bound certificate (which prevents it from having the private key stolen and used on another machine and requires only a TPM 1.2):

    ```powershell
    $tpmBoundCert = New-SelfSignedCertificate -Subject "Host Key Attestation ($env:computername)" -Provider "Microsoft Platform Crypto Provider"
    Set-HgsClientHostKey -Thumbprint $tpmBoundCert.Thumbprint
    ```
4. Get the public half of the key to provide to the HGS server. You can use the following cmdlet or, if you have the certificate stored elsewhere, provide a .cer containing the public half of the key. Note that we are only storing and validating the public key on HGS; we do not keep any certificate information nor do we validate the certificate chain or expiration date.

    ```powershell
    Get-HgsClientHostKey -Path "C:\temp\$env:hostname-HostKey.cer"
    ```
5. Copy the .cer file to your HGS server.

## Add the host key to the attestation service

This step is done on the HGS server and allows the host to run shielded VMs. It is recommended that you set the name to the FQDN or resource identifier of the host machine, so you can easily refer to which host the key is installed on.

```powershell
Add-HgsAttestationHostKey -Name MyHost01 -Path "C:\temp\MyHost01-HostKey.cer"
```