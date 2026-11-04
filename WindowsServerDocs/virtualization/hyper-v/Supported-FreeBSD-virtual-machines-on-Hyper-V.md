---
layout: Conceptual
title: Supported FreeBSD virtual machines on Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-freebsd-virtual-machines-on-hyper-v
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Lists the FreeBSD/Linux integration services and features included in each version
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-19T00:00:00.0000000Z
locale: en-us
document_id: fa3ffe77-3711-c87b-38e2-ed4be1155c9c
document_version_independent_id: c71759fa-c629-eae8-211e-1cd37a281718
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/Supported-FreeBSD-virtual-machines-on-Hyper-V.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/supported-freebsd-virtual-machines-on-hyper-v
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/Supported-FreeBSD-virtual-machines-on-Hyper-V.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 01a267a7-cee7-b463-d45e-e9f36c0e5760
---

# Supported FreeBSD virtual machines on Hyper-V | Microsoft Learn

The following feature distribution map indicates the features in each version. The known issues and workarounds for each distribution are listed after the table.

## Table legend

- **Built in** - BIS (FreeBSD Integration Service) are included as part of this FreeBSD release.
- ✔ - Feature available
- (*blank*) - Feature not available

| **Feature** | **Windows Server operating system version** | **13.0-13.5** | **12.0-12.4** | **11.0-11.4** |
| --- | --- | --- | --- | --- |
| **Availability** |  | Built in | Built in | Built in |
| **[Core](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#core)** | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Windows Server 2016 Accurate Time | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ |
| **[Networking](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#networking)** |  |  |  |  |
| Jumbo frames | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 2 | ✔ Note 2 | ✔ Note 2 |
| VLAN tagging and trunking | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Live migration | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Static IP Injection | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 3 | ✔ Note 3 | ✔ Note 3 |
| vRSS | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| TCP Segmentation and Checksum Offloads | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Large Receive Offload (LRO) | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| SR-IOV | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ |
| **[Storage](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#storage)** |  | Note 1 | Note1 | Note 1 |
| VHDX resize | 2025, 2022, 2019, 2016, 2012 R2 | ✔ Note 6 | ✔ Note 6 | ✔ Note 6 |
| Virtual Fibre Channel | 2025, 2022, 2019, 2016, 2012 R2 |  |  |  |
| Live virtual machine backup | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| TRIM support | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| SCSI WWN | 2025, 2022, 2019, 2016, 2012 R2 |  |  |  |
| **[Memory](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#memory)** |  |  |  |  |
| PAE Kernel Support | 2025, 2022, 2019, 2016, 2012 R2 |  |  |  |
| Configuration of MMIO gap | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Dynamic Memory - Hot-Add | 2025, 2022, 2019, 2016, 2012 R2 |  |  |  |
| Dynamic Memory - Ballooning | 2025, 2022, 2019, 2016, 2012 R2 |  |  |  |
| Runtime Memory Resize | 2025, 2022, 2019, 2016 |  |  |  |
| **[Video](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#video)** |  |  |  |  |
| Hyper-V specific video device | 2025, 2022, 2019, 2016, 2012 R2 |  |  |  |
| **[Miscellaneous](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#miscellaneous)** |  |  |  |  |
| Key/value pair | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Non-Maskable Interrupt | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| File copy from host to guest | 2025, 2022, 2019, 2016, 2012 R2 |  |  |  |
| lsvmbus command | 2025, 2022, 2019, 2016, 2012 R2 |  |  |  |
| Hyper-V Sockets | 2025, 2022, 2019, 2016 |  |  |  |
| PCI Passthrough/DDA | 2025, 2022, 2019, 2016 | ✔ | ✔ | ✔ |
| **[Generation 2 virtual machines](feature-descriptions-for-linux-and-freebsd-virtual-machines-on-hyper-v#generation-2-virtual-machines)** |  |  |  |  |
| Boot using UEFI | 2025, 2022, 2019, 2016, 2012 R2 | ✔ | ✔ | ✔ |
| Secure boot | 2025, 2022, 2019, 2016 |  |  |  |

## Notes

1. Suggest to [Label Disk Devices](https://www.freebsd.org/doc/handbook/geom-glabel.html) to avoid ROOT MOUNT ERROR during startup.
2. 9126 is the maximum supported MTU size.
3. In a failover scenario, you cannot set a static IPv6 address in the replica server. Use an IPv4 address instead.