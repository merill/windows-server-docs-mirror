---
layout: Conceptual
title: Obtain certificates for HGS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-obtain-certs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Obtain certificates for HGS'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2019-09-25T00:00:00.0000000Z
locale: en-us
document_id: 4110c62d-7118-ef73-fc5e-cafbf3b1eab2
document_version_independent_id: 5606b46b-c238-ad09-930a-666c44c1c222
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-obtain-certs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-obtain-certs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-obtain-certs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 81133a9a-cb8e-7197-fd4a-706b2555430a
---

# Obtain certificates for HGS | Microsoft Learn

When you deploy HGS, you will be asked to provide signing and encryption certificates that are used to protect the sensitive information needed to start up a shielded VM. These certificates never leave HGS, and are only used to decrypt shielded VM keys when the host on which they're running has proven it is healthy. Tenants (VM owners) use the public half of the certificates to authorize your datacenter to run their shielded VMs. This section covers the steps required to obtain compatible signing and encryption certificates for HGS.

## Request certificates from your certificate authority

While not required, it is strongly recommended that you obtain your certificates from a trusted certificate authority. Doing so helps VM owners verify that they are authorizing the correct HGS server (i.e. service provider or datacenter) to run their shielded VMs. In an enterprise scenario, you may choose to use your own enterprise CA to issue these certs. Hosters and service providers should consider using a well-known, public CA instead.

Both the signing and encryption certificates must be issued with the following certificiate properties (unless marked "recommended"):

| Certificate Template Property | Required value |
| --- | --- |
| Crypto provider | Any Key Storage Provider (KSP). Legacy Cryptographic Service Providers (CSPs) are **not** supported. |
| Key algorithm | RSA |
| Minimum key size | 2048 bits |
| Signature algorithm | Recommended: SHA256 |
| Key usage | Digital signature *and* data encipherment |
| Enhanced key usage | Server authentication |
| Key renewal policy | Renew with the same key. Renewing HGS certificates with different keys will prevent shielded VMs from starting up. |
| Subject name | Recommended: your company's name or web address. This information will be shown to VM owners in the shielding data file wizard. |

These requirements apply whether you are using certificates backed by hardware or software. For security reasons, it is recommended that you create your HGS keys in a Hardware Security Module (HSM) to prevent the private keys from being copied off the system. Follow the guidance from your HSM vendor to request certificates with the above attributes and be sure to install and authorize the HSM KSP on every HGS node.

Every HGS node will require access to the same signing and encryption certificates. If you are using software-backed certificates, you can export your certificates to a PFX file with a password and allow HGS to manage the certificates for you. You can also choose to install the certs into the local machine's certificate store on each HGS node and provide the thumbprint to HGS. Both options are explained in the [Initialize the HGS Cluster](guarded-fabric-initialize-hgs) topic.

## Create self signed certificates for test scenarios

If you are creating an HGS lab environment and do not have or want to use a certificate authority, you can create self-signed certificates. You will receive a warning when importing the certificate information in the shielding data file wizard, but all functionality will remain the same.

To create self-signed certificates and export them to a PFX file, run the following commands in PowerShell:

```powershell
$certificatePassword = Read-Host -AsSecureString -Prompt 'Enter a password for the PFX file'

$signCert = New-SelfSignedCertificate -Subject 'CN=HGS Signing Certificate' -KeyUsage DataEncipherment, DigitalSignature
Export-PfxCertificate -FilePath '.\signCert.pfx' -Password $certificatePassword -Cert $signCert

# Remove the certificate from "Personal" container
Remove-Item $signCert.PSPath
# Remove the certificate from "Intermediate certification authorities" container
Remove-Item -Path "Cert:\LocalMachine\CA\$($signCert.Thumbprint)"

$encCert = New-SelfSignedCertificate -Subject 'CN=HGS Encryption Certificate' -KeyUsage DataEncipherment, DigitalSignature
Export-PfxCertificate -FilePath '.\encCert.pfx' -Password $certificatePassword -Cert $encCert

# Remove the certificate from "Personal" container
Remove-Item $encCert.PSPath
# Remove the certificate from "Intermediate certification authorities" container
Remove-Item -Path "Cert:\LocalMachine\CA\$($encCert.Thumbprint)"
```

## Request an SSL certificate

All keys and sensitive information transmitted between Hyper-V hosts and HGS are encrypted at the message level -- that is, the information is encrypted with keys known either to HGS or Hyper-V, preventing someone from sniffing your network traffic and stealing keys to your VMs. However, if you have compliance requirements or simply prefer to encrypt all communications between Hyper-V and HGS, you can configure HGS with an SSL certificate which will encrypt all data at the transport level.

Both the Hyper-V hosts and HGS nodes will need to trust the SSL certificate you provide, so it is recommended that you request the SSL certificate from your enterprise certificate authority. When requesting the certificate, be sure to specify the following:

| SSL Certificate Property | Required value |
| --- | --- |
| Subject name | Address that HGS clients (that is, Guarded hosts) will be using to access the HGS server. This is typically the DNS address of your HGS cluster, known as the distributed network name or virtual computer object (VCO). This will be the concatenation of your HGS service name provided to `Initialize-HgsServer` and your HGS domain name. |
| Subject alternative name | If you will be using a different DNS name to reach your HGS cluster (e.g. if it is behind a load balancer, or you are using different addresses for a subset of nodes in complex topology), be sure to include those DNS names in the SAN field of your certificate request. Note that if SAN extension is populated, the Subject name is ignored, and hence SAN should include all values, including the one you would normally put in Subject name. |

The options for specifying this certificate when initializing the HGS server are covered in [Configure the first HGS node](guarded-fabric-initialize-hgs). You can also add or change the SSL certificate at a later time using the [Set-HgsServer](/en-us/powershell/module/hgsserver/set-hgsserver) cmdlet.