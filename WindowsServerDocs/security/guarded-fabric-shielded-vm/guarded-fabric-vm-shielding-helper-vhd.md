---
layout: Conceptual
title: Shielded VMs - Preparing a VM Shielding Helper VHD | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-vm-shielding-helper-vhd
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Shielded VMs - Preparing a VM Shielding Helper VHD'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: fe22d23a-9579-36c4-e3e2-62c02a986d8a
document_version_independent_id: 0d4f9362-afa5-aa67-635c-23adada467b3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-vm-shielding-helper-vhd.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-vm-shielding-helper-vhd
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-vm-shielding-helper-vhd.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f75b40f4-1ad1-f512-3eb6-6a8d2d3be9c3
---

# Shielded VMs - Preparing a VM Shielding Helper VHD | Microsoft Learn

Important

Before beginning these procedures, ensure that you have installed the latest cumulative update for Windows Server 2016 or are using the latest Windows 10 [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=45520). Otherwise, the procedures will not work.

This section outlines steps performed by a hosting service provider to enable support for converting existing VMs to shielded VMs.

To understand how this topic fits in the overall process of deploying shielded VMs, see [Hosting service provider configuration steps for guarded hosts and shielded VMs](guarded-fabric-configuration-scenarios-for-shielded-vms-overview).

## Which VMs can be shielded?

The shielding process for existing VMs is only available for VMs that meet the following prerequisites:

- The guest OS is Windows Server 2012, 2012 R2, 2016, or a Semi-Annual Channel release. Existing Linux VMs cannot be converted to shielded VMs.
- The VM is a generation 2 VM (UEFI firmware)
- The VM does not use differencing disks for its OS volume.

## Prepare Helper VHD

1. On a machine with Hyper-V and the Remote Server Administration Tools feature **Shielded VM Tools** installed, create a new generation 2 VM with a blank VHDX and install Windows Server 2016 on it using the Windows Server ISO installation media. This VM should not be shielded and must run Server Core or Server with Desktop Experience.

    Important

    The VM Shielding Helper VHD **must not** be related to the template disks you created in [Hosting service provider creates a shielded VM template](guarded-fabric-create-a-shielded-vm-template). If you re-use a template disk, there will be a disk signature collision during the shielding process because both disks will have the same GPT disk identifier. You can avoid this by creating a new (blank) VHD and installing Windows Server 2016 onto it using your ISO installation media.
2. Start the VM, complete any setup steps, and log into the desktop. Once you have verified the VM is in a working state, shut down the VM.
3. In an elevated Windows PowerShell window, run the following command to prepare the VHDX created earlier to become a VM shielding helper disk. Update the path with the correct path for your environment.

    ```powershell
    Initialize-VMShieldingHelperVHD -Path 'C:\VHD\shieldingHelper.vhdx'
    ```
4. Once the command has completed successfully, copy the VHDX to your VMM library share. **Do not** start up the VM from step 1 again. Doing so will corrupt the helper disk.
5. You can now delete the VM from step 1 in Hyper-V.

## Configure VMM Host Guardian Server Settings

In the VMM Console, open the settings pane and then **Host Guardian Service Settings** under **General**. At the bottom of this window, there is a field to configure the location of your helper VHD. Use the browse button to select the VHD from your library share. If you do not see your disk in the share, you may need to manually refresh the library in VMM for it to show up.

![VMM - Host Guardian Service Settings](../media/guarded-fabric-shielded-vm/guarded-host-vmm-hgs-settings-01.png)

## Additional References

- [Hosting service provider configuration steps for guarded hosts and shielded VMs](guarded-fabric-configuration-scenarios-for-shielded-vms-overview)
- [Guarded fabric and shielded VMs](guarded-fabric-and-shielded-vms-top-node)