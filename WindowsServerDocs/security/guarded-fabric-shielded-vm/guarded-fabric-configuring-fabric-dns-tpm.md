---
layout: Conceptual
title: Configure the fabric DNS for guarded hosts (TPM) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns-tpm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Next step'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: a9624871-ee1b-6697-0a0a-40d1c80dd6d0
document_version_independent_id: e57dfa55-d7e0-2d13-a7e2-a3f75efbaec2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns-tpm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns-tpm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configuring-fabric-dns-tpm.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a922d6af-d518-88f0-f765-b79a571aa25c
---

# Configure the fabric DNS for guarded hosts (TPM) | Microsoft Learn

There are many ways to configure name resolution for the fabric domain. One simple way is to set up a conditional forwarder zone in DNS for the fabric. To set up this zone, run the following commands in an elevated Windows PowerShell console on a fabric DNS server. Substitute the names and addresses in the Windows PowerShell syntax below as needed for your environment. Add the parameter `-MasterServers` for the additional HGS nodes.

```
Add-DnsServerConditionalForwarderZone -Name 'bastion.local' -ReplicationScope "Forest" -MasterServers <IP addresses of HGS server>
```

## Additional References

- [Configuration steps for Hyper-V hosts that will become guarded hosts](guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts)
- [Deployment tasks for guarded fabrics and shielded VMs](guarded-fabric-deploying-hgs-overview#deployment-tasks-for-guarded-fabrics-and-shielded-vms)