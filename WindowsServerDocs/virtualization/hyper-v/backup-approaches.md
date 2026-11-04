---
layout: Conceptual
title: Hyper-V Backup Approaches | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/backup-approaches
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Provides and describes the approaches for utilizing Hyper-V to create backup virtual machines.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2025-06-17T00:00:00.0000000Z
locale: en-us
document_id: f776fb66-ab2d-6107-86d2-ba3e4b9caf97
document_version_independent_id: f776fb66-ab2d-6107-86d2-ba3e4b9caf97
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/backup-approaches.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/backup-approaches
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/backup-approaches.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 8b8011b9-de09-bb49-391a-c4e6c8584121
---

# Hyper-V Backup Approaches | Microsoft Learn

Hyper-V allows you to backup virtual machines (VMs), from the host operating system, without the need to run custom backup software inside the virtual machine. There are several approaches that are available for developers to utilize depending on their needs.

You can do a VM backup or a data-only backup:

- **VM backup**: This approach backs up the entire virtual machine, including the configuration and all data. It's useful when you want to restore the entire VM to a previous state. Each virtual machine backup (full or incremental) must copy over all associated virtual machine configuration and virtual machine state files including virtual machine configuration (`.VMCX`), virtual machine guest state (`.VMGS`), and virtual machine runtime state (`.VMRS`) files. If you don't copy over all these files, the virtual machine state isn't fully captured.
- **Data-only backup**: This approach backs up only the data stored on the virtual hard disks of the virtual machine. To restore a data-only backup, you create a new virtual machine and restore the data to it.

## Hyper-V VSS Writer

Hyper-V implements a Volume Shadow Copy Service (VSS) writer on all versions of Windows Server where Hyper-V is supported. This VSS writer allows developers to utilize the existing VSS infrastructure to backup virtual machines. However, it's designed for small scale backup operations where all virtual machines on a server are backed up simultaneously.

## Hyper-V WMI Based Backup

Starting in Windows Server 2016, Hyper-V supports backup through the Hyper-V Windows Management Instrumentation (WMI) API. This approach still utilizes VSS inside the virtual machine for backup purposes, but no longer uses VSS in the host operating system. Instead, a combination of reference points and resilient change tracking (RCT) is used to allow developers to access the information about backed up virtual machines in an efficient manner. This approach is more scalable than using VSS in the host, however it's only available on Windows Server 2016 and later.

Learn more in the [Hyper-V WMI provider reference](/en-us/windows/win32/hyperv_v2/windows-virtualization-portal).

## Methods for reading backups from WMI Based Backup

When you create virtual machine backups using Hyper-V WMI, there are three methods for reading the actual data from the backup. Each has unique advantages and disadvantages.

### WMI Export

Developers can export the backup data through the Hyper-V WMI interfaces (as used in the previous example). Hyper-V compiles the changes into a virtual hard drive and copy the file to the requested location. This method is easy to use, works for all scenarios, and works remotely. However, the virtual hard drive generated often creates a large amount of data to transfer over the network.

### Win32 APIs

Developers can use the `SetVirtualDiskInformation`, `GetVirtualDiskInformation`, and `QueryChangesVirtualDisk` APIs on the Virtual Hard Disk Win32 API set as documented in the [Virtual Hard Disk Win32 reference](/en-us/windows/desktop/api/_vhd/). To use these APIs, Hyper-V WMI still needs to be used to create reference points on associated virtual machines. These Win32 APIs then allow for efficient access to the data of the backed up virtual machine. The Win32 APIs do have several limitations:

- They can only be accessed locally
- They don't support reading data from shared virtual hard disk files
- They return data addresses that are relative to the internal structure of the virtual hard disk

### Remote Shared Virtual Disk Protocol

Finally, if a developer needs to efficiently access backup data information from a shared virtual hard disk file, they need to use the Remote Shared Virtual Disk Protocol. This protocol is documented in the [Remote Shared Virtual Disk Protocol reference](/en-us/openspecs/windows_protocols/ms-rsvd/c865c326-47d6-4a91-a62d-0e8f26007d15).