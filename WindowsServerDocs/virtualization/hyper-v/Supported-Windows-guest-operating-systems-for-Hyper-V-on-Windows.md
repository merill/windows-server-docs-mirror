---
layout: Conceptual
title: Supported Windows guest operating systems for Hyper-V on Windows, Windows Server, and Azure Local | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-windows-guest-operating-systems-for-hyper-v-on-windows
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Lists the Windows operating systems supported for use as a guest in a virtual machine. Also gives links to similar articles for previous versions of Hyper-V.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-04-30T00:00:00.0000000Z
locale: en-us
document_id: cb311bf2-8548-000e-36a6-4ea4c01ac953
document_version_independent_id: d2966c17-b877-a879-bd7f-39c3758f0a77
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/Supported-Windows-guest-operating-systems-for-Hyper-V-on-Windows.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/supported-windows-guest-operating-systems-for-hyper-v-on-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/Supported-Windows-guest-operating-systems-for-Hyper-V-on-Windows.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 5f92819a-9865-42c9-8161-464d7f91d905
---

# Supported Windows guest operating systems for Hyper-V on Windows, Windows Server, and Azure Local | Microsoft Learn

Hyper-V supports several versions of Windows Server, Windows, and Linux distributions to run in virtual machines, as guest operating systems. This article covers supported Windows Server and Windows guest operating systems. For Linux and FreeBSD distributions, see [Supported Linux and FreeBSD virtual machines for Hyper-V on Windows](supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows).

Some operating systems have the integration services built-in. Others require that you install or upgrade integration services as a separate step after you set up the operating system in the virtual machine. For more information, see the following sections and [Integration Services](/en-us/virtualization/hyper-v-on-windows/reference/integration-services).

Guest operating systems configurable components are confined based on the hosting operating system. To learn more about the maximum configurable components in Hyper-V, see [Plan for Hyper-V scalability in Windows Server](maximum-scale-limits).

## Supported Windows Server guest operating systems

Following are the versions of Windows Server that are supported as guest operating systems for Hyper-V on Windows Server.

### Windows Server 2025

- **Maximum number of virtual processors**:
    - 2,048 for generation 2
    - 64 for generation 1
    - 2,048 available to the host OS (root partition)
- **Integration Services**: Built-in
- **Host operating systems**:
    - Windows Server 2022 and later
    - Azure Local OS, version 23H2 and later with Windows Server subscription.
- **Notes**:
    - Maximum number of virtual processors depends on the host OS. For example, Windows Server 2025 can provide up to 2,048 virtual processors.

### Windows Server 2022

- **Maximum number of virtual processors**:
    - 1,024 for generation 2
    - 64 for generation 1
    - 1,024 available to the host OS (root partition)
- **Integration Services**: Built-in
- **Host operating systems**:
    - Windows Server 2019 and later
    - Azure Local OS, version 23H2 and later.

### Windows Server 2019

- **Maximum number of virtual processors**:
    - 240 for generation 2
    - 64 for generation 1
    - 320 available to the host OS (root partition)
- **Integration Services**: Built-in

### Windows Server 2016

- **Maximum number of virtual processors**:
    - 240 for generation 2
    - 64 for generation 1
    - 320 available to the host OS (root partition)
- **Integration Services**: Built-in

### Windows Server 2012 R2

- **Maximum number of virtual processors**: 64
- **Integration Services**: Built-in

### Windows Server 2012

- **Maximum number of virtual processors**: 64
- **Integration Services**: Built-in

### Windows Server 2008 R2 with Service Pack 1 (SP1)

- **Maximum number of virtual processors**: 64
- **Integration Services**: Install all critical Windows updates after you set up the guest operating system.
- **Notes**: Datacenter, Enterprise, Standard, and Web editions.

### Windows Server 2008 with Service Pack 2 (SP2)

- **Maximum number of virtual processors**: 8
- **Integration Services**: Install all critical Windows updates after you set up the guest operating system.
- **Notes**: Datacenter, Enterprise, Standard, and Web editions (32-bit and 64-bit).

## Supported Windows client guest operating systems

Following are the versions of Windows client that are supported as guest operating systems for Hyper-V on Windows Server.

### Windows 11

- **Maximum number of virtual processors**: 32
- **Integration Services**: Built-in
- **Host operating systems**:
    - Generation 2 virtual machine hosted on Windows Server 2019 and later
    - Generation 2 virtual machine hosted on Azure Local OS, version 23H2 and later
- **Notes**:
    - Windows 11 requires an increased CPU instruction for installation and boot (POPCNT and SSE4.2). To meet these requirements in Hyper-V:
        - On Windows 11, Windows Server 2022 (standalone or clustered hosts), or standalone Windows Server 2025 hosts, disable processor compatibility to enable these features. Disabling processor compatibility limits live migration to hosts with the same processor features.
        - On Windows Server 2025 clusters with CPUs supporting POPCNT and SSE4.2, enable dynamic processor compatibility to ensure these features are available while retaining live migration capabilities within the cluster. To learn more about dynamic processor compatibility, see [Processor compatibility for Hyper-V virtual machines](processor-compatibility-mode).

### Windows 10

- **Maximum number of virtual processors**: 32
- **Integration Services**: Built-in

### Windows 8.1

- **Maximum number of virtual processors**: 32
- **Integration Services**: Built-in

### Windows 7 with Service Pack 1 (SP1)

- **Maximum number of virtual processors**: 4
- **Integration Services**: Upgrade the integration services after you set up the guest operating system.
- **Notes**: Ultimate, Enterprise, and Professional editions (32-bit and 64-bit).

## Supported Linux and FreeBSD

| Guest operating system |
| --- |
| [CentOS and Red Hat Enterprise Linux](/en-us/windows-server/virtualization/hyper-v/Supported-CentOS-and-Red-Hat-Enterprise-Linux-virtual-machines-on-Hyper-V) |
| [Debian virtual machines on Hyper-V](/en-us/windows-server/virtualization/hyper-v/Supported-Debian-virtual-machines-on-Hyper-V) |
| [SUSE](/en-us/windows-server/virtualization/hyper-v/Supported-SUSE-virtual-machines-on-Hyper-V) |
| [Oracle Linux](/en-us/windows-server/virtualization/hyper-v/Supported-Oracle-Linux-virtual-machines-on-Hyper-V) |
| [Ubuntu](/en-us/windows-server/virtualization/hyper-v/Supported-Ubuntu-virtual-machines-on-Hyper-V) |
| [FreeBSD](/en-us/windows-server/virtualization/hyper-v/Supported-FreeBSD-virtual-machines-on-Hyper-V) |

## How Microsoft provides support for guest operating systems

Microsoft provides support for guest operating systems in the following manner:

- Issues found in Microsoft operating systems and in integration services are supported by Microsoft support.
- For issues found in other operating systems that have been certified by the operating system vendor to run on Hyper-V, support is provided by the vendor.
- For issues found in other operating systems, Microsoft submits the issue to the multi-vendor support community, [TSANet](https://www.tsanet.org/).

In order to be supported, all operating systems (guest and host) must be up-to-date. Check Windows Update for critical updates.