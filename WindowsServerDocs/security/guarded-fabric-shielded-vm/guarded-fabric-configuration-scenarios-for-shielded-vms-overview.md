---
layout: Conceptual
title: Deploy shielded VMs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configuration-scenarios-for-shielded-vms-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Deploy shielded VMs'
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: edd505cb-5116-671a-5ff3-72e416953aee
document_version_independent_id: 3079e5db-6f47-9844-f5b3-bfd36e526192
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-configuration-scenarios-for-shielded-vms-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 19663726-b05c-be39-56f6-4e8f55f09303
---

# Deploy shielded VMs | Microsoft Learn

The following topics describe how a tenant can work with shielded VMs.

1. (Optional) [Create a Windows template disk](guarded-fabric-create-a-shielded-vm-template) or [create a Linux template disk](guarded-fabric-create-a-linux-shielded-vm-template). The template disk can be created by either the tenant or the hosting service provider.
2. (Optional) [Convert an existing Windows VM to a shielded VM](guarded-fabric-vm-shielding-helper-vhd).
3. [Create shielding data to define a shielded VM](guarded-fabric-tenant-creates-shielding-data).

    For a description and diagram of a shielding data file, see [What is shielding data and why is it necessary?](guarded-fabric-and-shielded-vms#what-is-shielding-data-and-why-is-it-necessary)

    For information about creating an answer file to include in a shielded data file, see [Shielded VMs - Generate an answer file by using the New-ShieldingDataAnswerFile function](guarded-fabric-sample-unattend-xml-file).
4. Create a shielded VM:

    - Using **Windows Azure Pack**: [Deploy a shielded VM by using Windows Azure Pack](guarded-fabric-shielded-vm-windows-azure-pack)
    - Using **Virtual Machine Manager**: [Deploy a shielded VM by using Virtual Machine Manager](guarded-fabric-tenant-deploys-shielded-vm-using-vmm)