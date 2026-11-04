---
layout: Conceptual
title: Configure the fabric DNS for guarded hosts (AD) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns-ad
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Configure the fabric DNS for guarded hosts (AD)'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: ea2e19b4-2c42-ad15-84ae-c3bfd8158c79
document_version_independent_id: 479c74dc-af35-213a-610e-f448130a21db
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns-ad.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns-ad
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns-ad.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: bb170e31-effb-3a1d-4908-54636d9871c4
---

# Configure the fabric DNS for guarded hosts (AD) | Microsoft Learn

Important

AD mode is deprecated beginning with Windows Server 2019. For environments where TPM attestation is not possible, configure [host key attestation](guarded-fabric-initialize-hgs-key-mode). Host key attestation provides similar assurance to AD mode and is simpler to set up.

A fabric administrator needs to configure the fabric DNS takes to allow guarded hosts to resolve the HGS cluster. The HGS cluster must already be set up by the [HGS administrator](/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs).

There are many ways to configure name resolution for the fabric domain. One simple way is to set up a conditional forwarder zone in DNS for the fabric. To set up this zone, run the following commands in an elevated Windows PowerShell console on a fabric DNS server. Substitute the names and addresses in the Windows PowerShell syntax below as needed for your environment. Add the parameter `-MasterServers` for the additional HGS nodes.

```
Add-DnsServerConditionalForwarderZone -Name 'bastion.local' -ReplicationScope "Forest" -MasterServers <IP addresses of HGS server>
```