---
layout: Conceptual
title: Supported SUSE Linux Enterprise Server (SLES) virtual machines on Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-suse-virtual-machines-on-hyper-v
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Learn about supported SUSE Linux Enterprise Server virtual machines on Hyper-V, including integration services and features. Compare versions and get deployment guidance.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-19T00:00:00.0000000Z
locale: en-us
document_id: f979eed9-9f75-a118-d95e-a33250003a49
document_version_independent_id: a4ee9607-c66b-a817-2916-beffd26cea9d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/Supported-SUSE-virtual-machines-on-Hyper-V.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/supported-suse-virtual-machines-on-hyper-v
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/Supported-SUSE-virtual-machines-on-Hyper-V.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 8db542bc-17c2-9dbf-3041-c23c1462bc18
---

# Supported SUSE Linux Enterprise Server (SLES) virtual machines on Hyper-V | Microsoft Learn

SUSE Linux Enterprise Server (SLES) is supported as a guest operating system on Hyper-V. This article provides a detailed overview of the integration services and features available for each supported SLES version. Use the included feature matrix to compare support across versions, and review the notes for important details, known issues, and recommended workarounds. This information helps you plan, deploy, and manage SLES virtual machines on Hyper-V with confidence.

The built-in SUSE Linux Enterprise Service drivers for Hyper-V are certified by SUSE. An example configuration can be viewed in this bulletin: [SUSE YES Certification Bulletin](https://www.suse.com/nbswebapp/yesBulletin.jsp?bulletinNumber=144176).

## Table legend for SLES virtual machine features

- **Built-in** - LIS are included as part of this Linux distribution. The Microsoft-provided LIS download package doesn't work for this distribution, so don't install it. The kernel module version numbers for the built-in LIS (as shown by **lsmod**, for example) are different from the version number on the Microsoft-provided LIS download package. A mismatch doesn't indicate that the built-in LIS is out of date.
- ✔ - Feature available
- (*blank*) - Feature not available

SLES12+ is 64-bit only.

| **Feature** | **Operating system version** | **SLES 15 SP1-SP7** | **SLES 15** | **SLES 12 SP3-SP5** | **SLES 12 SP2** | **SLES 12 SP1** | **SLES 11 SP4** | **SLES 11 SP3** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **Availability** |  | Built-in | Built-in | Built-in | Built in | Built-in | Built-in | Built-in |
| **[Core](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#core)** | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| Windows Server 2016 Accurate Time | WS/Hyper-V 2025,2022,2019,2016 | ✔ | ✔ | ✔ | ✔ |  |  |  |
| **[Networking](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#networking)** |  |  |  |  |  |  |  |  |
| Jumbo frames | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| VLAN tagging and trunking | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| Live migration | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| Static IP Injection | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔Note 1 | ✔Note 1 | ✔Note 1 | ✔Note 1 | ✔Note 1 | ✔Note 1 | ✔Note 1 |
| vRSS | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ |  |  |
| TCP Segmentation and Checksum Offloads | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |  |
| SR-IOV | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ |  |  |  |
| **[Storage](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#storage)** |  |  |  |  |  |  |  |  |
| VHDX resize | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| Virtual Fibre Channel | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| Live virtual machine backup | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ Note 2,3,8 | ✔Note 2,3,8 | ✔ Note 2,3,8 | ✔ Note 2,3,8 | ✔ Note 2,3,8 | ✔ Note 2,3,8 | ✔ Note 2,3,8 |
| TRIM support | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |  |
| SCSI WWN | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ |  |  |  |
| **[Memory](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#memory)** |  |  |  |  |  |  |  |  |
| PAE Kernel Support | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | N/A | N/A | N/A | N/A | N/A | ✔ | ✔ |
| Configuration of MMIO gap | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| Dynamic Memory - Hot-Add | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ Note 6 | ✔Note 6 | ✔ Note 6 | ✔ Note 6 | ✔ Note 6 | ✔ Note 4,5,6 | ✔ Note 4,5,6 |
| Dynamic Memory - Ballooning | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ Note 6 | ✔ Note 6 | ✔ Note 6 | ✔ Note 6 | ✔ Note 6 | ✔ Note 4,5,6 | ✔ Note 4,5,6 |
| Runtime Memory Resize | WS/Hyper-V 2025,2022,2019,2016 | ✔ Note 6 | ✔ Note 6 | ✔ Note 6 | ✔ Note 6 |  |  |  |
| **[Video](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#video)** |  |  |  |  |  |  |  |  |
| Hyper-V-specific video device | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| **[Miscellaneous](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#miscellaneous)** |  |  |  |  |  |  |  |  |
| Key/value pair | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ Note 7 | ✔ Note 7 |
| Non-Maskable Interrupt | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| File copy from host to guest | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |  |
| lsvmbus command | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ | ✔ | ✔ | ✔ |  |  |  |
| Hyper-V Sockets | WS/Hyper-V 2025,2022,2019,2016 | ✔ | ✔ | ✔ |  |  |  |  |
| PCI Passthrough/DDA | WS/Hyper-V 2025,2022,2019,2016 | ✔ | ✔ | ✔ | ✔ | ✔ |  |  |
| **[Generation 2 virtual machines](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#generation-2-virtual-machines)** |  |  |  |  |  |  |  |  |
| Boot using UEFI | WS/Hyper-V 2025,2022,2019,2016,2012 Azure Stack HCI | ✔ Note 9 | ✔ Note 9 | ✔ Note 9 | ✔ Note 9 | ✔ Note 9 | ✔ Note 9 |  |
| Secure boot | WS/Hyper-V 2025,2022,2019,2016 | ✔ | ✔ | ✔ | ✔ | ✔ |  |  |

## Notes

1. Static IP injection may not work if **NetworkManager** is configured for a given Hyper-V-specific network adapter on the virtual machine as it can override static IP settings that are manually configured. To ensure smooth functioning of static IP injection ensure that Network Manager is turned off completely or is turned off for a specific network adapter through its **ifcfg-ethX** file.
2. If there are open file handles during a live virtual machine backup operation, then in some corner cases, the backed-up VHDs might have to undergo a file system consistency check (fsck) on restore.
3. Live backup operations can fail silently if the virtual machine has an attached iSCSI device or direct-attached storage (also known as a pass-through disk).
4. Dynamic memory operations can fail if the guest operating system is running too low on memory. The following are some best practices:

    - Startup memory and minimal memory should be equal to or greater than the amount of memory that the distribution vendor recommends.
    - Applications that tend to consume the entire available memory on a system are limited to consuming up to 80 percent of available RAM.
5. Dynamic memory support is only available on 64-bit virtual machines.
6. If you're using Dynamic Memory on Windows Server 2016 or Windows Server 2012 operating systems, specify **Startup memory**, **Minimum memory**, and **Maximum memory** parameters in multiples of 128 megabytes (MB). Failure to do so can lead to Hot-Add failures, and you may not see any memory increase in a guest operating system.
7. In Windows Server 2016 or Windows Server 2012 R2, the key/value pair infrastructure might not function correctly without a Linux software update. Contact your distribution vendor to obtain the software update in case you see problems with this feature.
8. VSS backup fails if a single partition is mounted multiple times.
9. On Windows Server 2012 R2, Generation 2 virtual machines have secure boot enabled by default and Generation 2 Linux virtual machines don't boot unless the secure boot option is disabled. You can disable secure boot in the **Firmware** section of the settings for the virtual machine in Hyper-V Manager or you can disable it using PowerShell:

    ```Powershell
    Set-VMFirmware -VMName "VMname" -EnableSecureBoot Off
    ```