---
layout: Conceptual
title: Deploy NVMe Storage Devices using Discrete Device Assignment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/deploy/deploying-storage-devices-using-dda
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Learn how to use DDA to deploy storage devices
ms.topic: install-set-up-deploy
ms.author: roharwoo
author: robinharwood
ms.date: 2020-09-17T00:00:00.0000000Z
locale: en-us
document_id: f10da2ea-7f80-eaf0-da53-41c8b12aab30
document_version_independent_id: 18b715a7-2480-de55-badc-e3a35250e9c9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/deploy/Deploying-storage-devices-using-dda.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/deploy/deploying-storage-devices-using-dda
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/deploy/Deploying-storage-devices-using-dda.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 878b8755-9236-6fc8-a6ea-1672097be3f7
---

# Deploy NVMe Storage Devices using Discrete Device Assignment | Microsoft Learn

Starting with Windows Server 2016, you can use Discrete Device Assignment, or DDA, to pass an entire PCIe Device into a VM. This will allow high performance access to devices like NVMe storage or Graphics Cards from within a VM while being able to leverage the devices native drivers. Please visit the [Plan for Deploying Devices using Discrete Device Assignment](../plan/plan-for-deploying-devices-using-discrete-device-assignment) for more details on which devices work, what are the possible security implications, etc. There are three steps to using a device with DDA:

- Configure the VM for DDA
- Dismount the Device from the Host Partition
- Assigning the Device to the Guest VM

All command can be executed on the Host on a Windows PowerShell console as an Administrator.

## Configure the VM for DDA

Discrete Device Assignment imposes some restrictions to the VMs and the following step needs to be taken.

1. Configure the “Automatic Stop Action” of a VM to TurnOff by executing

```
Set-VM -Name VMName -AutomaticStopAction TurnOff
```

## Dismount the Device from the Host Partition

### Locating the Device's Location Path

The PCI Location path is required to dismount and mount the device from the Host. An example location path looks like the following: `"PCIROOT(20)#PCI(0300)#PCI(0000)#PCI(0800)#PCI(0000)"`. More details on located the Location Path can be found here: [Plan for Deploying Devices using Discrete Device Assignment](../plan/plan-for-deploying-devices-using-discrete-device-assignment).

### Disable the Device

Using Device Manager or PowerShell, ensure the device is “disabled.”

### Dismount the Device

```
Dismount-VMHostAssignableDevice -LocationPath $locationPath
```

## Assigning the Device to the Guest VM

The final step is to tell Hyper-V that a VM should have access to the device. In addition to the location path found above, you'll need to know the name of the vm.

```
Add-VMAssignableDevice -LocationPath $locationPath -VMName VMName
```

## What's Next

After a device is successfully mounted in a VM, you're now able to start that VM and interact with the device as you normally would if you were running on a bare metal system. You can verify this by opening device manager in the Guest VM and seeing that the hardware now shows up.

## Removing a Device and Returning it to the Host

If you want to return he device back to its original state, you will need to stop the VM and issue the following:

```
#Remove the device from the VM
Remove-VMAssignableDevice -LocationPath $locationPath -VMName VMName
#Mount the device back in the host
Mount-VMHostAssignableDevice -LocationPath $locationPath
```

You can then re-enable the device in device manager and the host operating system will be able to interact with the device again.