---
layout: Conceptual
title: Supported Oracle Linux virtual machines on Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-oracle-linux-virtual-machines-on-hyper-v
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Lists the Oracle Linux integration services and features included in each version
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-19T00:00:00.0000000Z
locale: en-us
document_id: ac3d04c7-6a13-1985-c003-85dc3579b012
document_version_independent_id: 82c87b00-49e8-1a48-fbe8-e99d8439fbea
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/Supported-Oracle-Linux-virtual-machines-on-Hyper-V.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/supported-oracle-linux-virtual-machines-on-hyper-v
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/Supported-Oracle-Linux-virtual-machines-on-Hyper-V.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 896a78be-24d4-ce1f-3876-a03fca1ce2df
---

# Supported Oracle Linux virtual machines on Hyper-V | Microsoft Learn

The following feature distribution map indicates the features that are present in each version. The known issues and workarounds for each distribution are listed after the table.

In this section:

- Oracle Linux 9.x Series
- Oracle Linux 8.x Series

## Table legend

- **Built in** - LIS are included as part of this Linux distribution. The kernel module version numbers for the built in LIS (as shown by **lsmod**, for example) are different from the version number on the Microsoft-provided LIS download package. A mismatch doesn't indicate that the built in LIS is out of date.
- ✔ - Feature available
- (*blank*) - Feature not available
- **RHCK** - Red Hat Compatible Kernel

## Oracle Linux 9.x Series

| **Feature** | **Windows Server version** | **9.0 (RHCK)** |
| --- | --- | --- |
| **Availability** |  |  |
| **[Core](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#core)** | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Windows Server 2016 Accurate Time | 2025, 2022, 2019, 2016 | ✔ |
| **[Networking](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#networking)** |  |  |
| Jumbo frames | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| VLAN tagging and trunking | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Live Migration | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Static IP Injection | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 1 |
| vRSS | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| TCP Segmentation and Checksum Offloads | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| SR-IOV | 2025, 2022, 2019, 2016 | ✔ |
| **[Storage](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#storage)** |  |  |
| VHDX resize | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Virtual Fibre Channel | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 2 |
| Live virtual machine backup | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 3 |
| TRIM support | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| SCSI WWN | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| **[Memory](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#memory)** |  |  |
| PAE Kernel Support | 2025, 2022, 2019, 2016, 2012 R2 | N/A |
| Configuration of MMIO gap | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Dynamic Memory - Hot-Add | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 4, 5, 6 |
| Dynamic Memory - Ballooning | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 4, 5, 6 |
| Runtime Memory Resize | 2025, 2022, 2019, 2016 | ✔ |
| **[Video](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#video)** |  |  |
| Hyper-V-specific video device | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| **[Miscellaneous](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#miscellaneous)** |  |  |
| Key-Value Pair | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Non-Maskable Interrupt | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| File copy from host to guest | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| lsvmbus command | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Hyper-V Sockets | 2025, 2022, 2019, 2016 | ✔ |
| PCI Passthrough/DDA | 2025, 2022, 2019, 2016 | ✔ |
| **[Generation 2 virtual machines](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#generation-2-virtual-machines)** |  |  |
| Boot using UEFI | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 7 |
| Secure boot | 2025, 2022, 2019, 2016 | ✔ |

## Oracle Linux 8.x Series

| **Feature** | **Windows Server version** | **8.0-8.5 (RHCK)** |
| --- | --- | --- |
| **Availability** |  |  |
| **[Core](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#core)** | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Windows Server 2016 Accurate Time | 2025, 2022, 2019, 2016 | ✔ |
| **[Networking](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#networking)** |  |  |
| Jumbo frames | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| VLAN tagging and trunking | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Live Migration | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Static IP Injection | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 1 |
| vRSS | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| TCP Segmentation and Checksum Offloads | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| SR-IOV | 2025, 2022, 2019, 2016 | ✔ |
| **[Storage](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#storage)** |  |  |
| VHDX resize | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Virtual Fibre Channel | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 2 |
| Live virtual machine backup | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 3 |
| TRIM support | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| SCSI WWN | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| **[Memory](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#memory)** |  |  |
| PAE Kernel Support | 2025, 2022, 2019, 2016, 2012 R2 | N/A |
| Configuration of MMIO gap | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Dynamic Memory - Hot-Add | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 4, 5, 6 |
| Dynamic Memory - Ballooning | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 4, 5, 6 |
| Runtime Memory Resize | 2025, 2022, 2019, 2016 | ✔ |
| **[Video](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#video)** |  |  |
| Hyper-V-specific video device | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| **[Miscellaneous](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#miscellaneous)** |  |  |
| Key-Value Pair | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Non-Maskable Interrupt | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| File copy from host to guest | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| lsvmbus command | 2025, 2022, 2019, 2016, 2012 R2 | ✔ |
| Hyper-V Sockets | 2025, 2022, 2019, 2016 | ✔ |
| PCI Passthrough/DDA | 2025, 2022, 2019, 2016 | ✔ |
| **[Generation 2 virtual machines](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#generation-2-virtual-machines)** |  |  |
| Boot using UEFI | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 7 |
| Secure boot | 2025, 2022, 2019, 2016 | ✔ |

## Notes

1. Static IP injection may not work if Network Manager has been configured for a given synthetic network adapter on the virtual machine. For smooth functioning of static IP injection please make sure that either Network Manager is either turned off completely or has been turned off for a specific network adapter through its ifcfg-ethX file.
2. On Windows Server 2012 R2 while using virtual fibre channel devices, make sure that logical unit number 0 (LUN 0) has been populated. If LUN 0 has not been populated, a Linux virtual machine might not be able to mount fibre channel devices natively.
3. If there are open file handles during a live virtual machine backup operation, then in some corner cases, the backed-up VHDs might have to undergo a file system consistency check (fsck) on restore. Live backup operations can fail silently if the virtual machine has an attached iSCSI device or direct-attached storage (also known as a pass-through disk).
4. Hot-Add support is not enabled by default in this distribution. To enable Hot-Add support you need to add a udev rule under /etc/udev/rules.d/ as follows:

    1. Create a file **/etc/udev/rules.d/100-balloon.rules**. You may use any other desired name for the file.
    2. Add the following content to the file: `SUBSYSTEM=="memory", ACTION=="add", ATTR{state}="online"`
    3. Reboot the system to enable Hot-Add support.

    While the Linux Integration Services download creates this rule on installation, the rule is also removed when LIS is uninstalled, so the rule must be recreated if dynamic memory is needed after uninstallation.
5. Dynamic memory operations can fail if the guest operating system is running too low on memory. The following are some best practices:

    - Startup memory and minimal memory should be equal to or greater than the amount of memory that the distribution vendor recommends.
    - Applications that tend to consume the entire available memory on a system are limited to consuming up to 80 percent of available RAM.
6. If you are using Dynamic Memory on a Windows Server 2016 or Windows Server 2012 R2 operating system, specify **Startup memory**, **Minimum memory**, and **Maximum memory** parameters in multiples of 128 megabytes (MB). Failure to do so can lead to hot-add failures, and you may not see any memory increase in a guest operating system.
7. On Windows Server 2012 R2 Generation 2 virtual machines have secure boot enabled by default and some Linux virtual machines will not boot unless the secure boot option is disabled. You can disable secure boot in the **Firmware** section of the settings for the virtual machine in **Hyper-V Manager** or you can disable it using PowerShell:

    ```Powershell
    Set-VMFirmware -VMName "VMname" -EnableSecureBoot Off
    ```

    The Linux Integration Services download can be applied to existing Generation 2 VMs but does not impart Generation 2 capability.