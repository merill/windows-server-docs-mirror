---
layout: Conceptual
title: Deploy guarded hosts | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Deploy guarded hosts'
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 51a46bd6-3e72-17c1-be81-3876b4be3ca1
document_version_independent_id: c54cac12-2b73-96ab-7be8-61c077377fed
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 514965ca-3e6d-2ac5-a279-54065b993a6d
---

# Deploy guarded hosts | Microsoft Learn

The topics in this section describe the steps that a fabric administrator takes to configure Hyper-V hosts to work with the Host Guardian Service (HGS). Before you can start these steps, at least one node in the [HGS cluster must be set up](guarded-fabric-setting-up-the-host-guardian-service-hgs).

**For TPM-trusted attestation**:

1. [Configure the fabric DNS](guarded-fabric-configuring-fabric-dns): Tells how to set up a DNS forwarder from the fabric domain to the HGS domain.
2. [Capture information required by HGS](guarded-fabric-tpm-trusted-attestation-capturing-hardware): Tells how to capture TPM identifiers (also called platform identifiers), create a Code Integrity policy, and create a TPM baseline. Then you will provide this information to the HGS administrator to configure attestation.
3. [Confirm guarded hosts can attest](guarded-fabric-confirm-hosts-can-attest-successfully)

**For host key attestation**:

1. [Create a host key](guarded-fabric-create-host-key#create-a-host-key): Tells how to set up a DNS forwarder from the fabric domain to the HGS domain.
2. [Add the host key to the attestation service](guarded-fabric-create-host-key#add-the-host-key-to-the-attestation-service): Tells how to set up an Active Directory security group in the fabric domain, add guarded hosts as members of that group, and provide that group identifier to the HGS administrator.
3. [Confirm guarded hosts can attest](guarded-fabric-confirm-hosts-can-attest-successfully)

**For Admin-trusted attestation**:

1. [Configure the fabric DNS](guarded-fabric-configuring-fabric-dns): Tells how to set up a DNS forwarder from the fabric domain to the HGS domain.
2. [Create a security group](guarded-fabric-admin-trusted-attestation-creating-a-security-group): Tells how to set up an Active Directory security group in the fabric domain, add guarded hosts as members of that group, and provide that group identifier to the HGS administrator.
3. [Confirm guarded hosts can attest](guarded-fabric-confirm-hosts-can-attest-successfully)

## Additional References

- [Deployment tasks for guarded fabrics and shielded VMs](guarded-fabric-deploying-hgs-overview#deployment-tasks-for-guarded-fabrics-and-shielded-vms)