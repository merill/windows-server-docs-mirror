---
layout: Conceptual
title: Enable Intel Performance Monitoring Hardware in a Hyper-V Virtual Machine | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/manage/performance-monitoring-hardware
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: How to enable Intel's Performance Monitoring Hardware in a Hyper-V Machine. Also touches on how enabling performance monitoring hardware effects live migration.
ms.reviewer: ifufondu
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2020-11-30T00:00:00.0000000Z
locale: en-us
document_id: 9d511241-f09a-63d9-e95b-99a52d93a14c
document_version_independent_id: c5897e9d-b827-04be-f894-59acf1474cf7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/manage/Performance-Monitoring-Hardware.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/manage/performance-monitoring-hardware
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/manage/Performance-Monitoring-Hardware.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b16a26c0-c394-88f2-ce32-9579f778abee
---

# Enable Intel Performance Monitoring Hardware in a Hyper-V Virtual Machine | Microsoft Learn

Intel processors contain features collectively called performance monitoring hardware (e.g. PMU, PEBS, LBR). These features are used by performance tuning software like Intel VTune Amplifier to analyze software performance. Prior to Windows Server 2019 and Windows 10 Version 1809, neither the host operating system nor Hyper-V guest virtual machines could use performance monitoring hardware when Hyper-V was enabled. Starting with Windows Server 2019 and Windows 10 Version 1809, the host operating system has access to performance monitoring hardware by default. Hyper-V guest virtual machines do not have access by default, but Hyper-V administrators may choose to grant access to one or more guest virtual machines. This document describes the steps required to expose performance monitoring hardware to guest virtual machines.

## Requirements

To enable performance monitoring hardware in a virtual machine, you'll need:

- An Intel processor with performance monitoring hardware (i.e. PMU, PEBS, LBR). Refer to [this document](https://software.intel.com/en-us/vtune-amplifier-cookbook-configuring-a-hyper-v-virtual-machine-for-hardware-based-hotspots-analysis) from Intel to determine which performance monitoring hardware your system supports.
- Windows Server 2019 or Windows 10 Version 1809 (October 2018 Update) or later
- A Hyper-V virtual machine *without*[nested virtualization](/en-us/virtualization/hyper-v-on-windows/user-guide/nested-virtualization) that is also in the stopped state

To enable upcoming Intel Processor Trace (IPT) performance monitoring hardware in a virtual machine, you’ll need:

- An Intel processor that supports IPT and the PT2GPA feature. [^1] Refer to [this document](https://software.intel.com/en-us/vtune-amplifier-cookbook-configuring-a-hyper-v-virtual-machine-for-hardware-based-hotspots-analysis) from Intel to determine which performance monitoring hardware your system supports.
- Windows Server version 1903 (SAC) or Windows 10 Version 1903 (May 2019 Update) or later
- A Hyper-V virtual machine *without*[nested virtualization](/en-us/virtualization/hyper-v-on-windows/user-guide/nested-virtualization) that is also in the stopped state
- PMU needs to be enabled via the command line using the command seen below.

[^1]: PT2GPA refers to the “Intel PT uses guest physical addresses” bit. This is described in 25.5.4.1 of the Intel SDM.

## Enabling performance monitoring components in a virtual machine

To enable different performance monitoring components for a specific guest virtual machine, use the `Set-VMProcessor` PowerShell cmdlet while running as Administrator:

Note

The virtual machine generation must be 9.1 or higher. If nested virtualization is offered to the guest as well, then this needs 9.3 and up.

```Powershell
# Enable IPT
Set-VMProcessor MyVMName -Perfmon @("ipt", "pmu")
```

```Powershell
# Enable all components
Set-VMProcessor MyVMName -Perfmon @("ipt", "pmu", "lbr", "pebs")
```

```Powershell
# Disable all components
Set-VMProcessor MyVMName -Perfmon @()
```

Note

When enabling the performance monitoring components, if `"pebs"` is specified, then `"pmu"` must also be specified. PEBS is only supported on hardware that has a PMU Version &gt;= 4. Also, any command that attempts to enable `"ipt"` must also specify `"pmu"`.

Enabling a component that is not supported by the host's physical processors will result in a virtual machine start failure.

## Effects of enabling performance monitoring hardware on save/restore, export, and live migration

Microsoft does not recommend live migrating or saving/restoring virtual machines with performance monitoring hardware between systems with different Intel hardware. The specific behavior of performance monitoring hardware is often non-architectural and changes between Intel hardware systems. Moving a running virtual machine between different systems can result in unpredictable behavior of the non-architectural counters.