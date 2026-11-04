---
layout: Conceptual
title: Install trusted TPM root certificates | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-install-trusted-tpm-root-certificates
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Install trusted TPM root certificates'
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2019-06-27T00:00:00.0000000Z
locale: en-us
document_id: 4fbb1fc3-8eca-4116-9eca-b568471c90e3
document_version_independent_id: eb4ae419-dce8-bf6d-bf64-2f7df6d8c2eb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-install-trusted-tpm-root-certificates.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-install-trusted-tpm-root-certificates
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-install-trusted-tpm-root-certificates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5069d6b3-5fbb-05a8-27f3-6815aa7de7ae
---

# Install trusted TPM root certificates | Microsoft Learn

When you configure HGS to use TPM attestation, you also need to configure HGS to trust the vendors of the TPMs in your servers. This extra verification process ensures only authentic, trustworthy TPMs are able to attest with your HGS. If you try to register an untrusted TPM with `Add-HgsAttestationTpmHost`, you will receive an error indicating the TPM vendor is untrusted.

To trust your TPMs, the root and intermediate signing certificates used to sign the endorsement key in your servers' TPMs need to be installed on HGS. If you use more than one TPM model in your datacenter, you may need to install different certificates for each model. HGS will look in the "TrustedTPM\_RootCA" and "TrustedTPM\_IntermediateCA" certificate stores for the vendor certificates.

Note

The TPM vendor certificates are different from those installed by default in Windows and represent the specific root and intermediate certificates used by TPM vendors.

A collection of trusted TPM root and intermediate certificates is published by Microsoft for your convenience. You can use the steps below to install these certificates. If your TPM certificates are not included in the package below, contact your TPM vendor or server OEM to obtain the root and intermediate certificates for your specific TPM model.

Repeat the following steps on **every HGS server**:

1. Download the latest package from https://go.microsoft.com/fwlink/?linkid=2097925.
2. Verify the signature of the cab file to ensure its authenticity. Do not proceed if the signature is not valid.

    ```powershell
    Get-AuthenticodeSignature .\TrustedTpm.cab
    ```

    Here's some example output:

    ```
    Directory: C:\Users\Administrator\Downloads
    
    SignerCertificate                         Status                                 Path
    -----------------                         ------                                 ----
    0DD6D4D4F46C0C7C2671962C4D361D607E370940  Valid                                  TrustedTpm.cab
    ```
3. Expand the cab file.

    ```
    mkdir .\TrustedTPM
    expand.exe -F:* <Path-To-TrustedTpm.cab> .\TrustedTPM
    ```
4. By default, the configuration script will install certificates for every TPM vendor. If you only want to import certificates for your specific TPM vendor, delete the folders for TPM vendors not trusted by your organization.
5. Install the trusted certificate package by running the setup script in the expanded folder.

    ```
    cd .\TrustedTPM
    .\setup.cmd
    ```

To add new certificates or ones intentionally skipped during an earlier installation, simply repeat the above steps on every node in your HGS cluster. Existing certificates will remain trusted but new certificates found in the expanded cab file will be added to the trusted TPM stores.