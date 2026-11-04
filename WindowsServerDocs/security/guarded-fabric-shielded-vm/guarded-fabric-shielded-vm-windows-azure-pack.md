---
layout: Conceptual
title: Shielded VMs  for tenants - Deploying a shielded VM by using Windows Azure Pack | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-shielded-vm-windows-azure-pack
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Shielded VMs  for tenants - Deploying a shielded VM by using Windows Azure Pack'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 508709a3-27f2-c74a-feb1-76e9f249a9aa
document_version_independent_id: fee118e1-6aec-4cb9-115e-1bbc601fbe0e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-shielded-vm-windows-azure-pack.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-shielded-vm-windows-azure-pack
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-shielded-vm-windows-azure-pack.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 65cb5218-8d6a-9cea-334d-dbee970b199c
---

# Shielded VMs  for tenants - Deploying a shielded VM by using Windows Azure Pack | Microsoft Learn

If your hosting service provider supports it, you can use Windows Azure Pack to deploy a shielded VM.

Complete the following steps:

1. Subscribe to one or more plans offered in Windows Azure Pack.
2. Create a shielded VM by using Windows Azure Pack.

    [Use shielded virtual machines](/en-us/previous-versions/azure/windows-server-azure-pack/mt720674%28v=technet.10%29), which is described in the following topics:

    - [Create shielding data](/en-us/previous-versions/azure/windows-server-azure-pack/mt720672%28v=technet.10%29) (and upload the shielding data file, as described in the second procedure in the topic).

        Note

        As part of creating shielding data, you will download your guardian key file, which will be an XML file in UTF-8 format. Do not change the file to UTF-16.
    - [Create a shielded virtual machine](/en-us/previous-versions/azure/windows-server-azure-pack/mt720673%28v=technet.10%29) - with **Quick Create**, through a shielded template, or through a regular template.

        Warning

        If you [Create a shielded virtual machine by using a regular template](/en-us/previous-versions/azure/windows-server-azure-pack/mt720673%28v=technet.10%29#Anchor_2), it is important to note that the VM is provisioned *unshielded*. This means that the template disk is not verified against the list of trusted disks in your shielding data file, nor are the secrets in your shielding data file used to provision the VM. If a shielded template is available, it is preferable to deploy a shielded VM with a shielded template to provide end-to-end protection of your secrets.
    - [Convert a Generation 2 virtual machine to a shielded virtual machine](/en-us/previous-versions/azure/windows-server-azure-pack/mt720670%28v=technet.10%29)

        Note

        If you convert a virtual machine to a shielded virtual machine, existing checkpoints and backups are not encrypted. You should delete old checkpoints when possible to prevent access to your old, decrypted data.

## Additional References

- [Hosting service provider configuration steps for guarded hosts and shielded VMs](guarded-fabric-configuration-scenarios-for-shielded-vms-overview)
- [Guarded fabric and shielded VMs](guarded-fabric-and-shielded-vms-top-node)