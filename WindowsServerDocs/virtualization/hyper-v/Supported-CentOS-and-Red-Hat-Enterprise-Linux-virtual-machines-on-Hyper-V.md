---
layout: Conceptual
title: CentOS and Red Hat Enterprise Linux VMs on Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-centos-and-red-hat-enterprise-linux-virtual-machines-on-hyper-v
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Lists the versions of Linux integration services for supported CentOS and Red Hat Enterprise distributions
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2025-06-19T00:00:00.0000000Z
locale: en-us
document_id: 988640af-813f-0ca3-8844-b09cf359f9cf
document_version_independent_id: 8be01cd9-2034-f44d-1016-3af62b7f0e15
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/supported-centos-and-red-hat-enterprise-linux-virtual-machines-on-hyper-v
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
platformId: 710d0d7f-42e7-a969-86bf-f7d91438247c
---

# CentOS and Red Hat Enterprise Linux VMs on Hyper-V | Microsoft Learn

The following feature distribution maps indicate the features that are present in built-in and downloadable versions of Linux Integration Services. The known issues and workarounds for each distribution are listed after the tables.

The built-in Red Hat Enterprise Linux Integration Services drivers for Hyper-V are sufficient for Red Hat Enterprise Linux guests to run using the high performance synthetic devices on Hyper-V hosts. These built-in drivers are certified by Red Hat for this use. Certified configurations can be viewed in the [Red Hat Certification Catalog](https://access.redhat.com/ecosystem/search/#/ecosystem/Red%20Hat%20Enterprise%20Linux?sort=sortTitle%20asc&amp;vendors=Microsoft&amp;category=Server).

It isn't necessary to download and install Linux Integration Services packages from the Microsoft Download Center, and doing so may limit your Red Hat support as described in [Red Hat Knowledgebase 1067](https://access.redhat.com/articles/1067).

Because of potential conflicts between the built-in LIS support and the downloadable LIS support when you upgrade the kernel, disable automatic updates, uninstall the LIS downloadable packages, update the kernel, reboot, and then install the latest LIS release, and reboot again.

In this section:

- RHEL/CentOS 10.x Series
- RHEL/CentOS 9.x Series
- RHEL/CentOS 8.x Series
- Notes

## Table legend

- **Built in** - LIS are included as part of this Linux distribution. The kernel module version numbers for the built-in LIS (as shown by **lsmod**, for example) are different from the version number on the Microsoft-provided LIS download package. A mismatch doesn't indicate that the built-in LIS is out of date.
- ✔ - Feature available
- (*blank*) - Feature not available

## RHEL/CentOS 10.x Series

| **Feature** | **Host OS** | **10.x** |
| --- | --- | --- |
| LIS Availability |  | Built in |
| [Core](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#core) | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Windows Server 2016 Accurate Time | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| &gt;256 vCPUs |  | ✔ |
| [Networking](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#networking) |  |  |
| Jumbo frames | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| VLAN tagging and trunking | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Live Migration | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Static IP Injection | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 2 |
| vRSS | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| TCP Segmentation and Checksum Offloads | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| SR-IOV | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| [Storage](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#storage) |  |  |
| VHDX resize | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Virtual Fibre Channel | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 3 |
| Live virtual machine backup | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 5 |
| TRIM support | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| SCSI WWN | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| [Memory](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#memory) |  |  |
| PAE Kernel Support | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI |  |
| Configuration of MMIO gap | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Dynamic Memory - Hot-Add | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 9, 10 |
| Dynamic Memory - Ballooning | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 9, 10 |
| Runtime Memory Resize | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| [Video](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#video) |  |  |
| Hyper-V-specific video device | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| [Miscellaneous](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#miscellaneous) |  |  |
| Key-Value Pair | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Non-Maskable Interrupt | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| File copy from host to guest | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| lsvmbus command | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Hyper-V Sockets | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| PCI Passthrough/DDA | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| [Generation 2 virtual machines](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#generation-2-virtual-machines) |  |  |
| Boot using UEFI | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 14, 17 |
| Secure boot | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |

## RHEL/CentOS 9.x Series

| **Feature** | **Host OS** | **9.x** |
| --- | --- | --- |
| LIS Availability |  | Built in |
| [Core](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#core) | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Windows Server 2016 Accurate Time | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| &gt;256 vCPUs |  | ✔ |
| [Networking](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#networking) |  |  |
| Jumbo frames | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| VLAN tagging and trunking | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Live Migration | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Static IP Injection | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 2 |
| vRSS | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| TCP Segmentation and Checksum Offloads | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| SR-IOV | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| [Storage](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#storage) |  |  |
| VHDX resize | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Virtual Fibre Channel | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 3 |
| Live virtual machine backup | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 5 |
| TRIM support | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| SCSI WWN | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| [Memory](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#memory) |  |  |
| PAE Kernel Support | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI |  |
| Configuration of MMIO gap | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Dynamic Memory - Hot-Add | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 9, 10 |
| Dynamic Memory - Ballooning | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 9,10 |
| Runtime Memory Resize | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| [Video](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#video) |  |  |
| Hyper-V-specific video device | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| [Miscellaneous](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#miscellaneous) |  |  |
| Key-Value Pair | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Non-Maskable Interrupt | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| File copy from host to guest | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| lsvmbus command | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| Hyper-V Sockets | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| PCI Passthrough/DDA | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |
| [Generation 2 virtual machines](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#generation-2-virtual-machines) |  |  |
| Boot using UEFI | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 14, 17 |
| Secure boot | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ |

## RHEL/CentOS 8.x Series

| **Feature** | **Host OS** | **8.1-8.6+** | **8.0** |
| --- | --- | --- | --- |
| LIS Availability |  | Built in | Built in |
| [Core](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#core) | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| Windows Server 2016 Accurate Time | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| &gt;256 vCPUs |  | ✔ |  |
| [Networking](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#networking) |  |  |  |
| Jumbo frames | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| VLAN tagging and trunking | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| Live Migration | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| Static IP Injection | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 2 | ✔ Note 2 |
| vRSS | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| TCP Segmentation and Checksum Offloads | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| SR-IOV | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| [Storage](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#storage) |  |  |  |
| VHDX resize | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| Virtual Fibre Channel | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 3 | ✔ Note 3 |
| Live virtual machine backup | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 5 | ✔ Note 5 |
| TRIM support | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| SCSI WWN | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| [Memory](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#memory) |  |  |  |
| PAE Kernel Support | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | N/A | N/A |
| Configuration of MMIO gap | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| Dynamic Memory - Hot-Add | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 9, 10 | ✔ Note 9, 10 |
| Dynamic Memory - Ballooning | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 9, 10 | ✔ Note 9, 10 |
| Runtime Memory Resize | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| [Video](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#video) |  |  |  |
| Hyper-V-specific video device | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| [Miscellaneous](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#miscellaneous) |  |  |  |
| Key-Value Pair | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| Non-Maskable Interrupt | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| File copy from host to guest | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| lsvmbus command | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| Hyper-V Sockets | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| PCI Passthrough/DDA | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |
| [Generation 2 virtual machines](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#generation-2-virtual-machines) |  |  |  |
| Boot using UEFI | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ Note 14, 17 | ✔ Note 14 |
| Secure boot | Windows Server 2025, 2022, 2019, 2016 Azure Stack HCI | ✔ | ✔ |

## RHEL/CentOS 7.x Series

This series only has 64-bit kernels.

| **Feature** | **Host OS** | **7.5-7.7** | **7.3-7.4** | **7.0-7.2** | **7.6-7.9** | **7.5** | **7.4** | **7.3** | **7.2** | **7.1** | **7.0** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| LIS Availability |  | [LIS 4.3](https://www.microsoft.com/download/details.aspx?id=55106) | [LIS 4.3](https://www.microsoft.com/download/details.aspx?id=55106) | [LIS 4.3](https://www.microsoft.com/download/details.aspx?id=55106) | Built-in | Built-in | Built-in | Built-in | Built-in | Built-in | Built-in |
| [Core](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#core) | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| Windows Server 2016 Accurate Time | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ |  | ✔ | ✔ | ✔ |  |  |  |  |
| &gt;256 vCPUs |  |  |  |  | ✔ Note 16 |  |  |  |  |  |  |
| [Networking](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#networking) |  |  |  |  |  |  |  |  |  |  |  |
| Jumbo frames | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| VLAN tagging and trunking | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| Live Migration | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| Static IP Injection | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 |
| vRSS | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |  |
| TCP Segmentation and Checksum Offloads | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |  |
| SR-IOV | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ |  | ✔ | ✔ | ✔ |  |  |  |  |
| [Storage](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#storage) |  |  |  |  |  |  |  |  |  |  |  |
| VHDX resize | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |  |  |
| Virtual Fibre Channel | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ Note 3 | ✔ Note 3 | ✔ Note 3 | ✔ Note 3 | ✔ Note 3 | ✔ Note 3 | ✔ Note 3 | ✔ Note 3 | ✔ Note 3 | ✔ Note 3 |
| Live virtual machine backup | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ Note 5 | ✔ Note 5 | ✔ Note 5 | ✔ Note 4,5 | ✔ Note 4,5 | ✔ Note 4, 5 | ✔ Note 4, 5 | ✔ Note 4, 5 | ✔ Note 4, 5 | ✔ Note 4, 5 |
| TRIM support | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |  |  |
| SCSI WWN | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ |  |  |  |  |  |  |
| [Memory](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#memory) |  |  |  |  |  |  |  |  |  |  |  |
| PAE Kernel Support | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | N/A | N/A | N/A | N/A | N/A | N/A | N/A | N/A | N/A | N/A |
| Configuration of MMIO gap | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| Dynamic Memory - Hot-Add | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ Note 8, 9, 10 | ✔ Note 8, 9, 10 | ✔ Note 8, 9, 10 | ✔ Note 8, 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 8, 9, 10 |
| Dynamic Memory - Ballooning | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 | ✔ Note 9, 10 |
| Runtime Memory Resize | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ |  |  |  |  |  |  |  |
| [Video](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#video) |  |  |  |  |  |  |  |  |  |  |  |
| Hyper-V-specific video device | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| [Miscellaneous](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#miscellaneous) |  |  |  |  |  |  |  |  |  |  |  |
| Key-Value Pair | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |
| Non-Maskable Interrupt | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| File copy from host to guest | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 | ✔ Note 4 |  |
| lsvmbus command | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ |  |  |  |  |  |  |  |
| Hyper-V Sockets | Windows Server 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ |  |  |  |  |  |  |  |
| PCI Passthrough/DDA | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ |  | ✔ | ✔ | ✔ | ✔ |  |  |  |
| [Generation 2 virtual machines](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#generation-2-virtual-machines) |  |  |  |  |  |  |  |  |  |  |  |
| Boot using UEFI | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ Note 14 | ✔ Note 14 | ✔ Note 14 | ✔ Note 14 | ✔ Note 14 | ✔ Note 14 | ✔ Note 14 | ✔ Note 14 | ✔ Note 14 | ✔ Note 14 |
| Secure boot | Windows Server 2025, 2022, 2019, 2016Azure Stack HCI | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |

## Notes

1. For this RHEL/CentOS release, VLAN tagging works but VLAN trunking doesn't.
2. Static IP injection may not work if Network Manager has been configured for a given synthetic network adapter on the virtual machine. For smooth functioning of static IP injection, make sure that either Network Manager is either turned off completely or has been turned off for a specific network adapter through its ifcfg-ethX file.
3. While using virtual fibre channel devices, make sure that logical unit number 0 (LUN 0) has been populated. If LUN 0 hasn't been populated, a Linux virtual machine might not be able to mount fibre channel devices natively.
4. For built-in LIS, the "hyperv-daemons" package must be installed for this functionality.
5. If there are open file handles during a live virtual machine backup operation, then in some corner cases, the backed-up VHDs might have to undergo a file system consistency check (fsck) on restore. Live backup operations can fail silently if the virtual machine has an attached iSCSI device or direct-attached storage (also known as a pass-through disk).
6. (Intentionally omitted for numbering consistency)
7. Dynamic memory support is only available on 64-bit virtual machines.
8. Hot-Add support isn't enabled by default in this distribution. To enable Hot-Add support you need to add a udev rule under /etc/udev/rules.d/ as follows:

    1. Create a file **/etc/udev/rules.d/100-balloon.rules**. You may use any other desired name for the file.
    2. Add the following content to the file: `SUBSYSTEM=="memory", ACTION=="add", ATTR{state}="online"`
    3. Reboot the system to enable Hot-Add support.

    While the Linux Integration Services download creates this rule on installation, the rule is also removed when LIS is uninstalled, so the rule must be recreated if dynamic memory is needed after uninstallation.
9. Dynamic memory operations can fail if the guest operating system is running too low on memory. The following are some best practices:

    - Startup memory and minimal memory should be equal to or greater than the amount of memory that the distribution vendor recommends.
    - Applications that tend to consume the entire available memory on a system are limited to consuming up to 80 percent of available RAM.
10. If you're using Dynamic Memory on Windows Server, specify **Startup memory**, **Minimum memory**, and **Maximum memory** parameters in multiples of 128 megabytes (MB). Failure to do so can lead to hot-add failures, and you may not see any memory increase in a guest operating system.
11. (Intentionally omitted for numbering consistency)
12. To enable key/value pair (KVP) infrastructure, install the hypervkvpd or hyperv-daemons rpm package from your RHEL ISO. Alternatively the package can be installed directly from RHEL repositories.
13. The key/value pair (KVP) infrastructure might not function correctly without a Linux software update. Contact your distribution vendor to obtain the software update in case you see problems with this feature.
14. Windows Server Generation 2 virtual machines have secure boot enabled by default and some Linux virtual machines will not boot unless the secure boot option is disabled. You can disable secure boot in the **Firmware** section of the settings for the virtual machine in **Hyper-V Manager** or you can disable it using PowerShell:

    ```powershell
    Set-VMFirmware -VMName "VMname" -EnableSecureBoot Off
    ```

    The Linux Integration Services download can be applied to existing Generation 2 VMs but doesn't impart Generation 2 capability.
15. RHEL 8.5 requires Windows Server 2019 or newer, or Azure Local 20H2 or newer.