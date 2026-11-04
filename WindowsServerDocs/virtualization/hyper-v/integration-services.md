---
layout: Conceptual
title: Hyper-V Integration Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/integration-services
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Reference for Hyper-V Integration Services
keywords: windows 10, hyper-v, integration services, integration components
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-29T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: ede699f7-c7ff-8afc-e5eb-f6de7e604560
document_version_independent_id: ede699f7-c7ff-8afc-e5eb-f6de7e604560
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/integration-services.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/integration-services
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/integration-services.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1e0cfd09-3e14-ae11-bd44-90b0621bcfef
---

# Hyper-V Integration Services | Microsoft Learn

Integration services, often called integration components, are services that allow the virtual machine to communicate with the Hyper-V host. Many of these services are conveniences, while others are important to the virtual machine's ability to function correctly.

This article is a reference for each integration service available in Windows. It also acts as a starting point for information related to specific integration services or their history.

For more information, see the Windows Server guide on [Managing integration services](/en-us/windows-server/virtualization/hyper-v/manage/Manage-Hyper-V-integration-services).

## Quick reference

| Name | Windows Service Name | Linux Daemon Name | Description | Impact on VM when disabled |
| --- | --- | --- | --- | --- |
| Hyper-V Heartbeat Service | `vmicheartbeat` | `hv_utils` | Reports that the virtual machine is running correctly. | Varies |
| Hyper-V Guest Shutdown Service | `vmicshutdown` | `hv_utils` | Allows the host to trigger virtual machines shutdown. | **High** |
| Hyper-V Time Synchronization Service | `vmictimesync` | `hv_utils` | Synchronizes the virtual machine's clock with the host computer's clock. | **High** |
| Hyper-V Data Exchange Service (KVP) | `vmickvpexchange` | `hv_kvp_daemon` | Provides a way to exchange basic metadata between the virtual machine and the host. | Medium |
| Hyper-V Volume Shadow Copy Requestor | `vmicvss` | `hv_vss_daemon` | Allows Volume Shadow Copy Service to back up the virtual machine without shutting it down. | Varies |
| Hyper-V Guest Service Interface | `vmicguestinterface` | `hv_fcopy_daemon` | Provides an interface for the Hyper-V host to copy files to or from the virtual machine. | Low |
| Hyper-V PowerShell Direct Service | `vmicvmsession` | not available | Provides a way to manage virtual machine with PowerShell without a network connection. | Low |

## Hyper-V heartbeat service

**Windows Service Name:** vmicheartbeat**Linux Daemon Name:** hv\_utils**Description:** Tells the Hyper-V host that the virtual machine has an operating system installed and that it booted correctly.**Added In:** Windows Server 2012, Windows 8**Impact:** When disabled, the virtual machine can't report that the operating system inside of the virtual machine is operating correctly. This limitation might affect some kinds of monitoring and host-side diagnostics.

The heartbeat service makes it possible to answer basic questions like "did the virtual machine boot?".

When Hyper-V reports that a virtual machine state is "running" (see the example in the following section), it means Hyper-V set aside resources for a virtual machine; it doesn't mean that an operating system is installed or functioning. This limitation is where heartbeat becomes useful. The heartbeat service tells Hyper-V that the operating system inside the virtual machine has booted.

### Check heartbeat with PowerShell

Run [Get-VM](/en-us/powershell/module/hyper-v/get-vm) as Administrator to see a virtual machine's heartbeat:

```PowerShell
Get-VM -VMName $VMName | select Name, State, Status
```

Your output should look something like this:

```output
Name    State    Status
----    -----    ------
DemoVM  Running  Operating normally
```

The `Status` field is determined by the heartbeat service.

## Hyper-V guest shutdown service

**Windows Service Name:**`vmicshutdown`**Linux Daemon Name:**`hv_utils`**Description:** Allows the Hyper-V host to request that the virtual machine shut down. The host can always force the virtual machine to turn off, but that action is like flipping the power switch as opposed to selecting shutdown.**Added In:** Windows Server 2012, Windows 8**Impact:** **High Impact** When disabled, the host can't trigger a friendly shutdown inside the virtual machine. All shutdowns are hard power-offs, which could cause data loss or data corruption.

## Hyper-V time synchronization service

**Windows Service Name:**`vmictimesync`**Linux Daemon Name:**`hv_utils`**Description:** Synchronizes the virtual machine's system clock with the system clock of the physical computer.**Added In:** Windows Server 2012, Windows 8**Impact:** **High Impact** When disabled, the virtual machine's clock drifts erratically.

## Hyper-V data exchange service (KVP)

**Windows Service Name:**`vmickvpexchange`**Linux Daemon Name:**`hv_kvp_daemon`**Description:** Provides a mechanism to exchange basic metadata between the virtual machine and the host.**Added In:** Windows Server 2012, Windows 8**Impact:** When disabled, virtual machines running Windows 8 or Windows Server 2012 or earlier don't receive updates to Hyper-V integration services. Disabling data exchange might also affect some kinds of monitoring and host-side diagnostics.

The data exchange service (sometimes called KVP) shares small amounts of machine information between virtual machine and the Hyper-V host by using key-value pairs (KVP) through the Windows registry. You can also use the same mechanism to share customized data between the virtual machine and the host.

Key-value pairs consist of a “key” and a “value”. Both the key and the value are strings, and no other data types are supported. When you create or change a key-value pair, both the guest and the host can see it. The key-value pair information transfers across the Hyper-V VMbus and doesn't require any kind of network connection between the guest and the Hyper-V host.

The data exchange service is a great tool for preserving information about the virtual machine. For interactive data sharing or data transfer, use PowerShell Direct.

Learn more about [Using key-value pairs to share information between the host and guest on Hyper-V](integration-services-data-exchange).

## Hyper-V Volume Shadow Copy Requestor

**Windows Service Name:**`vmicvss`**Linux Daemon Name:**`hv_vss_daemon`**Description:** Allows Volume Shadow Copy Service to back up applications and data on the virtual machine.**Added In:** Windows Server 2012, Windows 8**Impact:** When disabled, the virtual machine can't be backed up while running (using VSS).

The Volume Shadow Copy Requestor integration service is required for Volume Shadow Copy Service ([VSS](/en-us/windows/desktop/VSS/overview-of-processing-a-backup-under-vss)). The Volume Shadow Copy Service (VSS) captures and copies images for backup on running systems, particularly servers, without unduly degrading the performance and stability of the services they provide. This integration service makes that possible by coordinating the virtual machine's workloads with the host's backup process.

Read more about Volume Shadow Copy in [Backing Up and Restoring Virtual Machines](/en-us/windows/win32/hyperv_v2/backing-up-and-restoring-virtual-machines).

## Hyper-V Guest Service Interface

**Windows Service Name:**`vmicguestinterface`**Linux Daemon Name:**`hv_fcopy_daemon`**Description:** Provides an interface for the Hyper-V host to bidirectionally copy files to or from the virtual machine.**Added In:** Windows Server 2012 R2, Windows 8.1**Impact:** When disabled, the host can't copy files to and from the guest using `Copy-VMFile`. Read more about the [Copy-VMFile cmdlet](/en-us/powershell/module/hyper-v/copy-vmfile).

**Notes:** Disabled by default. See [PowerShell Direct using Copy-Item](powershell-direct#copy-files-with-new-pssession-and-copy-item).

## Hyper-V PowerShell Direct Service

**Windows Service Name:**`vmicvmsession`**Linux Daemon Name:** n/a**Description:** Provides a mechanism to manage a virtual machine with PowerShell through a VM session without a virtual network. **Added In:** Windows Server TP3, Windows 10**Impact:** If you disable this service, the host can't connect to the virtual machine with PowerShell Direct.

**Notes:** The service name was originally Hyper-V VM Session Service. PowerShell Direct is under active development and is only available on Windows 10/Windows Server Technical Preview 3 or later hosts and guests.

PowerShell Direct enables PowerShell management inside a virtual machine from the Hyper-V host, regardless of any network configuration or remote management settings on either the Hyper-V host or the virtual machine. This feature makes it easier for Hyper-V administrators to automate and script management and configuration tasks.

The following resources might be helpful for managing PowerShell Direct:

- [PowerShell Direct](powershell-direct).
    - [Running script in a virtual machine](powershell-direct#run-a-script-or-command-with-invoke-command)
    - [Copying files to and from a virtual machine](powershell-direct#copy-files-with-new-pssession-and-copy-item)