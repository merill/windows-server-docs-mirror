---
layout: Conceptual
title: Initialize the HGS cluster using TPM mode in a new dedicated forest (default) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode-default
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Initialize the HGS cluster using TPM mode in a new dedicated forest (default)'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 8fcd846e-32f9-c5c1-8522-582baac6240e
document_version_independent_id: 97308239-844e-9432-3580-34cad539bdee
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode-default.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode-default
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode-default.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 15519296-7dfc-f659-0676-13f156f91220
---

# Initialize the HGS cluster using TPM mode in a new dedicated forest (default) | Microsoft Learn

1. Clients can easily contact any HGS node by using the failover clustering distributed network name (DNN). You'll need to choose a DNN. This name will be registered in the HGS DNS service. As an example, if you have 3 HGS nodes with hostnames HGS01, HGS02, and HGS03, you might decide to choose "hgs" or "HgsCluster" for the DNN.
2. Locate your HGS guardian certificates. You will need one signing certificate and one encryption certificate to initialize the HGS cluster. The easiest way to provide certificates to HGS is to create a password-protected PFX file for each certificate which contains both the public and private keys. If you are using HSM-backed keys or other non-exportable certificates, make sure the certificate is installed into the local machine's certificate store before continuing. For more information about which certificates to use, see [Obtain certificates for HGS](/en-us/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-obtain-certs).
3. Run [Initialize-HgsServer](/en-us/powershell/module/hgsserver/initialize-hgsserver) in an elevated PowerShell window on the first HGS node. The syntax of this cmdlet supports many different inputs, but the 2 most common invocations are below:

    - If you are using PFX files for your signing and encryption certificates, run the following commands:

        ```powershell
        $signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
        $encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"
        
        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signingCertPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustTpm
        ```
    - If you are using non-exportable certificates that are installed in the local certificate store, run the following command. If you do not know the thumbprints of your certificates, you can list available certificates by running `Get-ChildItem Cert:\LocalMachine\My`.

        ```powershell
        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificateThumbprint '1A2B3C4D5E6F...' -EncryptionCertificateThumbprint '0F9E8D7C6B5A...' -TrustTpm
        ```
4. If you provided any certificates to HGS using thumbprints, you will be instructed to grant HGS read access to the private key of those certificates. On a server with Desktop Experience installed, complete the following steps:

    1. Open the local computer certificate manager (**certlm.msc**)
    2. Find the certificate(s) &gt; right-click &gt; all tasks &gt; manage private keys
    3. Click **Add**
    4. In the object picker window, click **Object types** and enable **service accounts**
    5. Enter the name of the service account mentioned in the warning text from `Initialize-HgsServer`
    6. Ensure the gMSA has "Read" access to the private key.

    On server core, you will need to download a PowerShell module to assist in setting the private key permissions.

    1. Run `Install-Module GuardedFabricTools` on the HGS server if it has Internet connectivity, or run `Save-Module GuardedFabricTools` on another computer and copy the module over to the HGS server.
    2. Run `Import-Module GuardedFabricTools`. This will add additional properties to certificate objects found in PowerShell.
    3. Find your certificate thumbprint in PowerShell with `Get-ChildItem Cert:\LocalMachine\My`
    4. Update the ACL, replacing the thumbprint with your own and the gMSA account in the code below with the account listed in the warning text of `Initialize-HgsServer`.

        ```powershell
        $certificate = Get-Item "Cert:\LocalMachine\1A2B3C..."
        $certificate.Acl = $certificate.Acl | Add-AccessRule "HgsSvc_1A2B3C" Read Allow
        ```

    If you are using HSM-backed certificates, or certificates stored in a third party key storage provider, these steps may not apply to you. Consult your key storage provider's documentation to learn how to manage permissions on your private key. In some cases, there is no authorization, or authorization is provided to the entire computer when the certificate is installed.
5. That's it! In a production environment, you should continue to [add additional HGS nodes to your cluster](/en-us/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-configure-additional-hgs-nodes).