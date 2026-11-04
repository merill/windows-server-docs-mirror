---
layout: Conceptual
title: Supported Debian virtual machines on Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-debian-virtual-machines-on-hyper-v
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Learn about the Debian and Linux integration services and features included in each version and known issues and workarounds for each distribution.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-19T00:00:00.0000000Z
locale: en-us
document_id: b46eaa07-8134-fb75-5322-d6896a8f3a1b
document_version_independent_id: 562af23a-e5ed-33eb-c539-bd2a6a442d17
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/Supported-Debian-virtual-machines-on-Hyper-V.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/supported-debian-virtual-machines-on-hyper-v
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/Supported-Debian-virtual-machines-on-Hyper-V.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d3f034bf-07b3-d830-dbfd-f33f06f8be11
---

# Supported Debian virtual machines on Hyper-V | Microsoft Learn

This article outlines the support offered for Debian virtual machines (VMs) on Hyper-V.

## Table legend

The following feature distribution map indicates the features that are present in each version of Windows Server. The known issues and workarounds for each distribution are listed after the table.

- **Built-in LIS** - Linux integration services (LIS) are included as part of this Linux distribution. The Microsoft-provided LIS download package doesn't work for this distribution. Don't install the Microsoft package. The kernel module version numbers for the built-in LIS (as shown by **lsmod**, for example) are different from the version number on the Microsoft-provided LIS download package. A mismatch doesn't indicate that the built-in LIS is out of date.
- ✔ - Feature available
- (*blank*) - Feature not available

| **Feature** | **Windows Server Hyper-V version** | **12 (Bookworm)** | **11 (Bullseye)** | **10 (Buster)** |
| --- | --- | --- | --- | --- |
| **Availability** |  | Built-in LIS | Built-in LIS | Built-in LIS |
| **[Core](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#core)** | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Windows Server 2016 Accurate Time | 2025, 2022, 2019, 2016 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| **[Networking](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#networking)** |  |  |  |  |
| Jumbo frames | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| VLAN tagging and trunking | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Live Migration | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Static IP Injection | 2025, 2022, 2019, 2016, 2012 R2 |  |  |  |
| vRSS | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| TCP Segmentation and Checksum Offloads | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| SR-IOV | 2025, 2022, 2019, 2016 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| **[Storage](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#storage)** |  |  |  |  |
| VHDX resize | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 1 | ✔ Note 1 | ✔ Note 1 |
| Virtual Fibre Channel | 2025, 2022, 2019, 2016, 2012 R2 |  |  |  |
| Live virtual machine backup | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 |
| TRIM support | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| SCSI WWN | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| **[Memory](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#memory)** |  |  |  |  |
| PAE Kernel Support | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Configuration of MMIO gap | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Dynamic Memory - Hot-Add | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| Dynamic Memory - Ballooning | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| Runtime Memory Resize | 2025, 2022, 2019, 2016 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| **[Video](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#video)** |  |  |  |  |
| Hyper-V-specific video device | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| **[Miscellaneous](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#miscellaneous)** |  |  |  |  |
| Key-Value Pair | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 |
| Non-Maskable Interrupt | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| File copy from host to guest | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 |
| lsvmbus command | 2025, 2022, 2019, 2016, 2012 R2 |  |  |  |
| Hyper-V Sockets | 2025, 2022, 2019, 2016 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| PCI Passthrough/DDA | 2025, 2022, 2019, 2016 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| **[Generation 2 virtual machines](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#generation-2-virtual-machines)** |  |  |  |  |
| Boot using UEFI | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 3 | ✔ Note 3 | ✔ Note 3 |
| Secure boot | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ |

## Notes

1. Creating file systems on VHDs larger than 2 TB isn't supported.
2. Starting with Debian 8.3, the manually installed Debian package "hyperv-daemons" contains the key-value pair, fcopy, and VSS daemons. On Debian 7.x and 8.0-8.2, the hyperv-daemons package must come from [Debian backports](https://wiki.debian.org/Backports).
3. On Windows Server 2012 R2, Generation 2 virtual machines have secure boot enabled by default, and some Linux virtual machines don't boot unless the secure boot option is disabled. You can disable secure boot in the **Firmware** section of the settings for the virtual machine in **Hyper-V Manager**, or you can disable it by using PowerShell:

    ```powershell
    Set-VMFirmware -VMName "VMname" -EnableSecureBoot Off
    ```
4. The latest upstream kernel capabilities are only available by using the kernels available in the [Debian backports repository](https://wiki.debian.org/Backports).