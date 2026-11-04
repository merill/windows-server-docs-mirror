---
layout: Conceptual
title: Supported Ubuntu virtual machines on Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-ubuntu-virtual-machines-on-hyper-v
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Lists the Ubuntu/Linux integration services and features included in each version of Windows Server.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-02-19T00:00:00.0000000Z
locale: en-us
document_id: 84d52296-198d-7c8a-db99-e8cb336e355f
document_version_independent_id: 77670399-109f-3233-0466-c13d84542039
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/Supported-Ubuntu-virtual-machines-on-Hyper-V.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/supported-ubuntu-virtual-machines-on-hyper-v
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/Supported-Ubuntu-virtual-machines-on-Hyper-V.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 4dc14d1e-f6a5-26d5-1ab7-3ce3cbca1c82
---

# Supported Ubuntu virtual machines on Hyper-V | Microsoft Learn

The following feature distribution map indicates the features in each version. The known issues and workarounds for each distribution are listed after the table.

## Table legend

- **Built in** - Linux Integration Services (LIS) is included as part of this Linux distribution. The Microsoft-provided LIS download package doesn't work for this distribution, so don't install it. The kernel module version numbers for the built in LIS (as shown by **lsmod**, for example) are different from the version number on the Microsoft-provided LIS download package. A mismatch doesn't indicate that the built in LIS is out of date.
- ✔ - Feature available
- (*blank*) - Feature not available

| **Feature** | **Windows Server operating system version** | **24.04 LTS** | **22.04 LTS** | **20.04 LTS** | **18.04 LTS** | **16.04 LTS** |
| --- | --- | --- | --- | --- | --- | --- |
| **Availability** |  | Built-in | Built-in | Built-in | Built-in | Built-in |
| **[Core](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#core)** | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| Windows Server 2016 Accurate Time | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| **[Networking](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#networking)** |  |  |  |  |  |  |
| Jumbo frames | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| VLAN tagging and trunking | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| Live migration | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| Static IP Injection | 2025, 2022, 2019, 2016 | ✔ Note 1 | ✔ Note 1 | ✔ Note 1 | ✔ Note 1 | ✔ Note 1 |
| vRSS | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| TCP Segmentation and Checksum Offloads | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| SR-IOV | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| **[Storage](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#storage)** |  |  |  |  |  |  |
| VHDX resize | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| Virtual Fibre Channel | 2025, 2022, 2019, 2016 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 |
| Live virtual machine backup | 2025, 2022, 2019, 2016 | ✔ Note 3, 4, 5 | ✔ Note 3, 4, 5 | ✔ Note 3, 4, 5 | ✔ Note 3, 4, 5 | ✔ Note 3, 4, 5 |
| TRIM support | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| SCSI WWN | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| **[Memory](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#memory)** |  |  |  |  |  |  |
| PAE Kernel Support | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| Configuration of MMIO gap | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| Dynamic Memory - Hot-Add | 2025, 2022, 2019, 2016 | ✔ Note 6, 7, 8 | ✔ Note 6, 7, 8 | ✔ Note 6, 7, 8 | ✔ Note 6, 7, 8 | ✔ Note 6, 7, 8 |
| Dynamic Memory - Ballooning | 2025, 2022, 2019, 2016 | ✔ Note 6, 7, 8 | ✔ Note 6, 7, 8 | ✔ Note 6, 7, 8 | ✔ Note 6, 7, 8 | ✔ Note 6, 7, 8 |
| Runtime Memory Resize | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| **[Video](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#video)** |  |  |  |  |  |  |
| Hyper-V specific video device | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| **[Miscellaneous](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#miscellaneous)** |  |  |  |  |  |  |
| Key/value pair | 2025, 2022, 2019, 2016 | ✔ Note 5, 9 | ✔ Note 5, 9 | ✔ Note 5, 9 | ✔ Note 5, 9 | ✔ Note 5, 9 |
| Non-Maskable Interrupt | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| File copy from host to guest | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| lsvmbus command | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| Hyper-V Sockets | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| PCI Passthrough/DDA | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |
| **[Generation 2 virtual machines](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#generation-2-virtual-machines)** |  |  |  |  |  |  |
| Boot using UEFI | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ Note 10, 11 | ✔ Note 10, 11 | ✔ Note 10, 11 |
| Secure boot | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ | ✔ | ✔ |

## Notes

1. Static IP injection may not work if **NetworkManager** has been configured for a given Hyper-V-specific network adapter on the virtual machine as it can override static IP settings that have been manually configured. To ensure smooth functioning of static IP injection, ensure that Network Manager is turned off completely or has been turned off for a specific network adapter through its **ifcfg-ethX** file.
2. While using virtual fiber channel devices, ensure that logical unit number 0 (LUN 0) has been populated. If LUN 0 hasn't been populated, a Linux virtual machine might not be able to mount fiber channel devices natively.
3. If there are open file handles during a live virtual machine backup operation, then in some corner cases, the backed-up VHDs might have to undergo a file system consistency check (`fsck`) on restore.
4. Live backup operations can fail silently if the virtual machine has an attached iSCSI device or direct-attached storage (also known as a pass-through disk).
5. On long term support (LTS) releases use latest virtual Hardware Enablement (HWE) kernel for up to date Linux Integration Services.

    To install the Azure-tuned kernel on Ubuntu, run the following commands as root (or sudo):

    ```bash
    # apt-get update
    # apt-get install linux-azure
    ```
6. Dynamic memory support is only available on 64-bit virtual machines.
7. Dynamic Memory operations can fail if the guest operating system is running too low on memory. The following are some best practices:

    - Startup memory and minimal memory should be equal to or greater than the amount of memory that the distribution vendor recommends.
    - Applications that tend to consume the entire available memory on a system are limited to consuming up to 80 percent of available RAM.
8. If you're using Dynamic Memory on Windows Server, specify **Startup memory**, **Minimum memory**, and **Maximum memory** parameters in multiples of 128 megabytes (MB). Failure to do so can lead to Hot-Add failures, and you might not see any memory increase on a guest operating system.
9. In Windows Server 2019, and Windows Server 2016, the key/value pair infrastructure might not function correctly without a Linux software update. Contact your distribution vendor to obtain the software update in case you see problems with this feature.
10. Generation 2 virtual machines have secure boot enabled by default and some Linux virtual machines won't boot unless the secure boot option is disabled. You can disable secure boot in the **Firmware** section of the settings for the virtual machine in **Hyper-V Manager** or you can disable it using PowerShell:

    ```Powershell
    Set-VMFirmware -VMName "VMname" -EnableSecureBoot Off
    ```
11. Before attempting to copy the VHD of an existing Generation 2 VHD virtual machine to create new Generation 2 virtual machines, follow these steps:

    1. Log in to the existing Generation 2 virtual machine.
    2. Change directory to the boot EFI directory:

        ```bash
        # cd /boot/efi/EFI
        ```
    3. Copy the ubuntu directory in to a new directory named boot:

        ```bash
        # sudo cp -r ubuntu/ boot
        ```
    4. Change directory to the newly created boot directory:

        ```bash
        # cd boot
        ```
    5. Rename the shimx64.efi file:

        ```bash
        # sudo mv shimx64.efi bootx64.efi
        ```
12. In order to perform live migrations for VMs that are Generation 2 configured, the **Migrate to a physical computer with a different processor version** option must be enabled under *Processor* &gt; *Compatibility* in your VM settings. To learn more, see [Processor compatibility mode in Hyper-V](manage/processor-compatibility-mode-hyper-v).