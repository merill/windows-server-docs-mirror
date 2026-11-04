---
layout: Conceptual
title: Cmdlets for configuring persistent memory devices for Hyper-V VMs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/manage/persistent-memory-cmdlets
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: How to configure persistent memory devices for Hyper-V VMs
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2026-01-21T00:00:00.0000000Z
locale: en-us
document_id: b1123d54-7f3a-d5ea-c224-4bf9fbec3c96
document_version_independent_id: 097b96eb-eeab-9bed-ff12-7809565a6e6f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/manage/persistent-memory-cmdlets.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/manage/persistent-memory-cmdlets
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/manage/persistent-memory-cmdlets.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: b43edf9a-287f-f80c-950f-08ea9a75c46d
---

# Cmdlets for configuring persistent memory devices for Hyper-V VMs | Microsoft Learn

This article provides system administrators and IT Pros with information about configuring Hyper-V VMs with persistent memory (also known as storage class memory or NVDIMM). JEDEC-compliant NVDIMM-N persistent memory devices are supported in Windows Server 2016 and Windows 10 and provide byte-level access to very low latency nonvolatile devices. VM persistent memory devices are supported in Windows Server 2019.

## Create a persistent memory device for a VM

Use the **[New-VHD](/en-us/powershell/module/hyper-v/new-vhd)** cmdlet to create a persistent memory device for a VM. The device must be created on an existing NTFS DAX volume. The new filename extension (.vhdpmem) is used to specify that the device is a persistent memory device. Only the fixed VHD file format is supported.

**Example:**`New-VHD D:\VMPMEMDevice1.vhdpmem -Fixed -SizeBytes 4GB`

## Create a VM with a persistent memory controller

Use the **New-VM cmdlet** to create a Generation 2 VM with specified memory size and path to a VHDX image. Then, use **Add-VMPmemController** to add a persistent memory controller to a VM.

**Example:**

```powershell
New-VM -Name "ProductionVM1" -MemoryStartupBytes 1GB -VHDPath c:\vhd\BaseImage.vhdx

Add-VMPmemController -VMName "ProductionVM1"
```

## Attach a persistent memory device to a VM

Use **[Add-VMHardDiskDrive](/en-us/powershell/module/hyper-v/add-vmharddiskdrive)** to attach a persistent memory device to a VM

**Example:**`Add-VMHardDiskDrive -VMName "ProductionVM1" -ControllerType PMEM -ControllerLocation 1 -Path D:\VMPMEMDevice1.vhdpmem`

Persistent memory devices within a Hyper-V VM appear as a persistent memory device to be consumed and managed by the guest operating system. Guest operating systems can use the device as a block or DAX volume. When persistent memory devices within a VM are used as a DAX volume, they benefit from low latency byte-level address-ability of the host device (no I/O virtualization on the code path).

Note

Persistent memory is only supported for Hyper-V Gen2 VMs. Live Migration and Storage Migration are not supported for VMs with persistent memory. Production checkpoints of VMs do not include persistent memory state.