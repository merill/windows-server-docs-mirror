---
layout: Conceptual
title: Guarded fabric and shielded VMs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms-top-node
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Guarded fabric and shielded VMs'
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: d3d97834-a7a2-2e9b-f9fd-1025e038388e
document_version_independent_id: dbf305e8-49e1-c8be-f4fb-d056912c76b9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms-top-node.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms-top-node
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms-top-node.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: a643cf09-5257-41ba-a0e8-589d3801a051
---

# Guarded fabric and shielded VMs | Microsoft Learn

One of the most important goals of providing a hosted environment is to guarantee the security of the virtual machines running in the environment. As a cloud service provider or enterprise private cloud administrator, you can use a guarded fabric to provide a more secure environment for VMs. A guarded fabric consists of one Host Guardian Service (HGS) - typically, a cluster of three nodes - plus one or more guarded hosts, and a set of shielded virtual machines (VMs).

Important

Ensure that you have installed the latest cumulative update before you deploy shielded virtual machines in production.

## Videos, blog, and overview topic about guarded fabrics and shielded VMs

- Video: [How to protect your virtualization fabric from insider threats with Windows Server 2019](/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-compatible-hardware-with-virtualization-based-protection-of-code-integrity)
- Video: Introduction to Shielded Virtual Machines in Windows Server 2016
- Video: Dive into Shielded VMs with Windows Server 2016 Hyper-V
- Video: [Deploying Shielded VMs and a Guarded Fabric with Windows Server 2016](https://mva.microsoft.com/training-courses/deploying-shielded-vms-and-a-guarded-fabric-with-windows-server-2016-17131?l=WFLef7vUD_4604300474)
- Blog: [Datacenter and Private Cloud Security Blog](/en-us/archive/blogs/datacentersecurity/)
- Overview: [Guarded fabric and shielded VMs overview](guarded-fabric-and-shielded-vms)

## Planning topics

- [Planning guide for hosters](guarded-fabric-planning-for-hosters)
- [Planning guide for tenants](guarded-fabric-shielded-vm-planning-for-tenants)

## Deployment topics

- [Deployment Guide](guarded-fabric-deploying-hgs-overview)
    - [Quick start](guarded-fabric-deployment-overview)
    - [Deploy HGS](guarded-fabric-setting-up-the-host-guardian-service-hgs)
    - [Deploy guarded hosts](guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts)
        - [Configuring the fabric DNS for hosts that will become guarded hosts](guarded-fabric-configuring-fabric-dns)
        - [Deploy a guarded host using AD mode](guarded-fabric-admin-trusted-attestation-creating-a-security-group)
        - [Deploy a guarded host using TPM mode](guarded-fabric-tpm-trusted-attestation-capturing-hardware)
        - [Confirm guarded hosts can attest](guarded-fabric-confirm-hosts-can-attest-successfully)
        - [Shielded VMs - Hosting service provider deploys guarded hosts in VMM](/en-us/system-center/vmm/guarded-deploy-host)
    - [Deploy shielded VMs](guarded-fabric-configuration-scenarios-for-shielded-vms-overview)
        - [Create a shielded VM template](guarded-fabric-create-a-shielded-vm-template)
        - [Prepare a VM Shielding helper VHD](guarded-fabric-vm-shielding-helper-vhd)
        - [Set up Windows Azure Pack](guarded-fabric-hoster-sets-up-windows-azure-pack)
        - [Create a shielding data file](guarded-fabric-tenant-creates-shielding-data)
        - [Deploy a shielded VM by using Windows Azure Pack](guarded-fabric-shielded-vm-windows-azure-pack)
        - [Deploy a shielded VM by using Virtual Machine Manager](guarded-fabric-tenant-deploys-shielded-vm-using-vmm)

## Operations and management topic

- [Managing the Host Guardian Service](guarded-fabric-manage-hgs)