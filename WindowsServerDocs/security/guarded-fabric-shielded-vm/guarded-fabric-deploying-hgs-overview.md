---
layout: Conceptual
title: Deploying the Host Guardian Service | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-deploying-hgs-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Deploying the Host Guardian Service'
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2020-01-14T00:00:00.0000000Z
locale: en-us
document_id: 848c4b83-046b-d091-d772-6dca2da0f77d
document_version_independent_id: b18b5b35-f528-761c-b2e1-8e4aca59cdbe
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-deploying-hgs-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-deploying-hgs-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-deploying-hgs-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: 9d937e26-42e4-eb1b-39fa-cf2b96d97817
---

# Deploying the Host Guardian Service | Microsoft Learn

One of the most important goals of providing a hosted environment is to guarantee the security of the virtual machines running in the environment. As a cloud service provider or enterprise private cloud administrator, you can use a guarded fabric to provide a more secure environment for VMs. A guarded fabric consists of one Host Guardian Service (HGS) - typically, a cluster of three nodes - plus one or more guarded hosts, and a set of shielded virtual machines (VMs).

## Video: Deploying a guarded fabric

## Deployment tasks for guarded fabrics and shielded VMs

The following table breaks down the tasks to deploy a guarded fabric and create shielded VMs according to different administrator roles. Note that when the HGS admin configures HGS with authorized Hyper-V hosts, a fabric admin will collect and provide identifying information about the hosts at the same time.

| Step and link to content | Image |
| --- | --- |
| 1 - [Verify HGS prerequisites](guarded-fabric-prepare-for-hgs) | ![Step 1, verify prerequisites](../media/guarded-fabric-shielded-vm/guarded-host-verify.png) |
| 2 - [Configure first HGS node](guarded-fabric-choose-where-to-install-hgs) | ![Step 2, configure the first HGS node](../media/guarded-fabric-shielded-vm/guarded-host-configure-first-hgs-node.png) |
| 3 - [Configure additional HGS nodes](guarded-fabric-configure-additional-hgs-nodes) | ![Step 3, configure additional HGS nodes](../media/guarded-fabric-shielded-vm/guarded-host-configure-secondary-hgs-nodes.png) |
| 4 - [Configure fabric DNS](guarded-fabric-configuring-fabric-dns) | ![Step 4, configure fabric DNS](../media/guarded-fabric-shielded-vm/guarded-host-configure-fabric-dns.png) |
| 5 - [Verify host prerequisites (Key)](guarded-fabric-guarded-host-prerequisites#host-key-attestation) and [Verify host prerequisites (TPM)](guarded-fabric-guarded-host-prerequisites#tpm-trusted-attestation) | ![Step 5, verify host prerequisite key and host prerequisite TPM](../media/guarded-fabric-shielded-vm/guarded-host-verify.png) |
| 6 - [Create host key (Key)](guarded-fabric-create-host-key) and[Collect host information (TPM)](guarded-fabric-tpm-trusted-attestation-capturing-hardware) | ![Step 6, create host key and collect host info](../media/guarded-fabric-shielded-vm/guarded-host-collect-info-from-hosts.png) |
| 7 - [Configure HGS with host information](guarded-fabric-add-host-information-to-hgs) | ![Step 7, add host info to HGS](../media/guarded-fabric-shielded-vm/guarded-host-configure-hgs-with-host-info.png) |
| 8 - [Confirm hosts can attest](guarded-fabric-confirm-hosts-can-attest-successfully) | ![Step 8, confirm host can attest](../media/guarded-fabric-shielded-vm/guarded-host-confirm-hosts-attest.png) |
| 9 - [Configure VMM (optional)](/en-us/system-center/vmm/deploy-guarded-host-fabric) | ![Step 9, configure VMM (optional)](../media/guarded-fabric-shielded-vm/guarded-host-configure-vmm.png) |
| 10 - [Create template disks](guarded-fabric-create-a-shielded-vm-template) | ![Step 10, create template disks](../media/guarded-fabric-shielded-vm/guarded-host-create-template-disk.png) |
| 11 - [Create a VM shielding helper disk for VMM (optional)](guarded-fabric-vm-shielding-helper-vhd) | ![Step 11, create a VM shielding help disk for VMM](../media/guarded-fabric-shielded-vm/guarded-host-create-helper-disk.png) |
| 12 - [Set up Windows Azure Pack (optional)](guarded-fabric-shielded-vm-windows-azure-pack) | ![Step 12, set up Windows Azure Pack (optional)](../media/guarded-fabric-shielded-vm/guarded-host-windows-azure-pack.png) |
| 13 - [Create shielding data file](guarded-fabric-tenant-creates-shielding-data) | ![Step 13, create a shielding data file](../media/guarded-fabric-shielded-vm/guarded-host-shielding-data-file.png) |
| 14 - [Create shielded VMs using Windows Azure Pack](guarded-fabric-shielded-vm-windows-azure-pack) | ![Step 14, create shielded VMs using Windows Azure Pack](../media/guarded-fabric-shielded-vm/guarded-host-shielded-vms.png) |
| 15 - [Create shielded VMs using VMM](/en-us/system-center/vmm/guarded-deploy-vm) | ![Step 15, create shielded VMs using VMM](../media/guarded-fabric-shielded-vm/guarded-host-shielded-vms.png) |

## Additional References

- [Guarded fabric and shielded VMs](guarded-fabric-and-shielded-vms-top-node)