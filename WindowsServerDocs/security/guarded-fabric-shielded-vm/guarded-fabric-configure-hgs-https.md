---
layout: Conceptual
title: Configure HGS for HTTPS communications | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-https
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Configure HGS for HTTPS communications'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 1c47b720-0973-0a5e-1c2f-b2165aba71d6
document_version_independent_id: 762e9c78-b8f8-79d3-4934-f3f1e91e579e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-https.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-https
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-https.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ffaf82c7-0ba7-4fdc-9392-5edda90c62a2
---

# Configure HGS for HTTPS communications | Microsoft Learn

By default, when you initialize the HGS server it will configure the IIS web sites for HTTP-only communications. All sensitive material being transmitted to and from HGS are always encrypted using message-level encryption, however if you desire a higher level of security you can also enable HTTPS by configuring HGS with an SSL certificate.

First, obtain an SSL certificate for HGS from your certificate authority. Each host machine will need to trust the SSL certificate, so it is recommended that you issue the SSL certificate from your company's public key infrastructure or a third party CA. Any SSL certificate supported by IIS is supported by HGS, however **the subject name on the certificate must match the fully qualified HGS service name** (cluster distributed network name). For instance, if the HGS domain is "bastion.local" and your HGS service name is "hgs", your SSL certificate should be issued for "hgs.bastion.local". You can add additional DNS names to the certificate's subject alternative name field if necessary.

Once you have the SSL certificate, open an elevated PowerShelll session and either provide the certificate path when you run [Set-HgsServer](/en-us/powershell/module/hgsserver/set-hgsserver):

```powershell
$sslPassword = Read-Host -AsSecureString -Prompt "SSL Certificate Password"
Set-HgsServer -Http -Https -HttpsCertificatePath 'C:\temp\HgsSSLCertificate.pfx' -HttpsCertificatePassword $sslPassword
```

Or, if you have already installed the certificate into the local certificate store, you can reference it by thumbprint:

```powershell
Set-HgsServer -Http -Https -HttpsCertificateThumbprint 'A1B2C3D4E5F6...'
```

Important

Configuring HGS with an SSL certificate does not disable the HTTP endpoint. If you wish to only allow use of the HTTPS endpoint, configure Windows Firewall to block inbound connections to port 80. **Do not modify the IIS bindings** for HGS websites to remove the HTTP endpoint; it is unsupported to do so.