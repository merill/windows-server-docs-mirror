---
layout: Conceptual
title: Configure the fabric DNS for guarded hosts | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Configure the fabric DNS for guarded hosts'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 9d150d86-ca7f-4e65-7b0a-0d744f81fb1b
document_version_independent_id: bcade7de-bed2-a4e0-520b-446df57ec0c3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c8e7b549-ba1d-7a9a-d8d0-97df68670b3a
---

# Configure the fabric DNS for guarded hosts | Microsoft Learn

A fabric administrator needs to configure the fabric DNS takes to allow guarded hosts to resolve the HGS cluster. The HGS cluster must already be set up by the [HGS administrator](/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-initialize-hgs).

There are many ways to configure name resolution for the fabric domain. One simple way is to set up a conditional forwarder zone in DNS for the fabric. To set up this zone, run the following commands in an elevated Windows PowerShell console on a fabric DNS server. Substitute the names and addresses in the Windows PowerShell syntax below as needed for your environment. Add the parameter `-MasterServers` for the additional HGS nodes.

```
Add-DnsServerConditionalForwarderZone -Name 'bastion.local' -ReplicationScope "Forest" -MasterServers <IP addresses of HGS server>
```