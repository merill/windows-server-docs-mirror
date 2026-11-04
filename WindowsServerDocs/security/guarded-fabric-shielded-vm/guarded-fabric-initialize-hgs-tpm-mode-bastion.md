---
layout: Conceptual
title: Initialize the HGS cluster using TPM mode in a bastion forest | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode-bastion
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Initialize the HGS cluster using TPM mode in an existing bastion forest'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 6ae25db7-fa78-b9bd-463c-a6debe7387f9
document_version_independent_id: 9384ad42-9e6a-ecd6-b07f-7baf55cbe4eb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode-bastion.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode-bastion
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs-tpm-mode-bastion.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7c01134-b8f3-438c-822d-13471e513908
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/82fff6b2-939d-4e9a-8f9c-d1c41a59749b
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: f0db4beb-2b32-a27e-3bdc-2a97fcf9149d
---

# Initialize the HGS cluster using TPM mode in a bastion forest | Microsoft Learn

To initialize the HGS cluster using TPM mode in an existing bastion forest, follow the steps below. Active Directory Domain Services will be installed on the machine, but should remain unconfigured.

Locate your HGS guardian certificates. You will need one signing certificate and one encryption certificate to initialize the HGS cluster. The easiest way to provide certificates to HGS is to create a password-protected PFX file for each certificate which contains both the public and private keys. If you are using HSM-backed keys or other non-exportable certificates, make sure the certificate is installed into the local machine's certificate store before continuing. For more information about which certificates to use, see [Obtain certificates for HGS](/en-us/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-obtain-certs).

Before you continue, ensure that you have prestaged your cluster objects for the Host Guardian Service and granted the logged in user **Full Control** over the VCO and CNO objects in Active Directory. The virtual computer object name needs to be passed to the `-HgsServiceName` parameter, and the cluster name to the `-ClusterName` parameter.

Tip

Double check your AD Domain Controllers to ensure your cluster objects have replicated to all DCs before continuing.

If you are using PFX-based certificates, run the following commands on the HGS server:

```powershell
$signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
$encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"

Install-ADServiceAccount -Identity 'HGSgMSA'

Initialize-HgsServer -UseExistingDomain -ServiceAccount 'HGSgMSA' -JeaReviewersGroup 'HgsJeaReviewers' -JeaAdministratorsGroup 'HgsJeaAdmins' -HgsServiceName 'HgsService' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustTpm
```

If you are using certificates installed on the local machine (such as HSM-backed certificates and non-exportable certificates), use the `-SigningCertificateThumbprint` and `-EncryptionCertificateThumbprint` parameters instead.

In a production environment, you should continue to [add additional HGS nodes to your cluster](guarded-fabric-configure-additional-hgs-nodes).