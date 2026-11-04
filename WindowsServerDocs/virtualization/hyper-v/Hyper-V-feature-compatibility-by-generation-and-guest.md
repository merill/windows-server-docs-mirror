---
layout: Conceptual
title: Hyper-V feature compatibility by generation and guest | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/hyper-v-feature-compatibility-by-generation-and-guest
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Lists the generations and operating systems that are compatible with key Hyper-V features
ms.topic: feature-availability
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-19T00:00:00.0000000Z
locale: en-us
document_id: f83a16dd-56e2-83e8-68d1-c2d928e5e031
document_version_independent_id: 12a96354-e1bb-3568-3a8e-84925d28b825
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/Hyper-V-feature-compatibility-by-generation-and-guest.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/hyper-v-feature-compatibility-by-generation-and-guest
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/Hyper-V-feature-compatibility-by-generation-and-guest.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 17178fb3-7d55-0581-46d2-664674e51568
---

# Hyper-V feature compatibility by generation and guest | Microsoft Learn

The tables in this article show you the generations and operating systems that are compatible with some of the Hyper-V features, grouped by categories. In general, you'll get the best availability of features with a generation 2 virtual machine that runs the newest operating system.

Keep in mind that some features rely on hardware or other infrastructure. For hardware details, see [System requirements for Hyper-V on Windows Server](host-hardware-requirements). In some cases, a feature can be used with any supported guest operating system. For details on which operating systems are supported, see:

- [Supported Linux and FreeBSD virtual machines](supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows)
- [Supported Windows guest operating systems](supported-windows-guest-operating-systems-for-hyper-v-on-windows)

## Availability and backup

| Feature | Generation | Guest operating system |
| --- | --- | --- |
| Checkpoints | 1 and 2 | Any supported guest |
| Guest clustering | 1 and 2 | Guests that run cluster-aware applications and have iSCSI target software installed |
| Replication | 1 and 2 | Any supported guest |
| Domain Controller | 1 and 2 | Any supported Windows Server guest using only production checkpoints. See [Supported Windows Server guest operating systems](supported-windows-guest-operating-systems-for-hyper-v-on-windows#supported-windows-server-guest-operating-systems) |

## Compute

| Feature | Generation | Guest operating system |
| --- | --- | --- |
| Dynamic memory | 1 and 2 | Specific versions of supported guests. See [Hyper-V Dynamic Memory Overview](dynamic-memory). |
| Hot add/removal of memory | 1 and 2 | Windows Server 2016, Windows 10 |
| Virtual NUMA | 1 and 2 | Any supported guest |

## Development and test

| Feature | Generation | Guest operating system |
| --- | --- | --- |
| COM/Serial ports | 1 and 2 | Any supported guest |

Note

For generation 2 COM/Serial ports, use Windows PowerShell to configure. For details, see [Add a COM port for kernel debugging](plan/should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v#add-a-com-port-for-kernel-debugging).

## Mobility

| Feature | Generation | Guest operating system |
| --- | --- | --- |
| Live migration | 1 and 2 | Any supported guest |
| Import/export | 1 and 2 | Any supported guest |

## Networking

| Feature | Generation | Guest operating system |
| --- | --- | --- |
| Hot add/removal of virtual network adapter | 2 | Any supported guest |
| Legacy virtual network adapter | 1 | Any supported guest |
| Single root input/output virtualization (SR-IOV) | 1 and 2 | 64-bit Windows guests, starting with Windows Server 2012 and Windows 8. |
| Virtual machine multi queue (VMMQ) | 1 and 2 | Any supported guest |

## Remote connection experience

| Feature | Generation | Guest operating system |
| --- | --- | --- |
| Discrete device assignment (DDA) | 1 and 2 | Windows Server 2012 and later, Windows 10 and Windows 11 |
| Enhanced session mode | 1 and 2 | Windows Server 2012 R2 and later, and Windows 8.1 and later, with Remote Desktop Services enabled. |
| RemoteFx | 1 and 2 | Generation 1 on 32-bit and 64-bit Windows versions starting with Windows 8; Generation 2 on 64-bit Windows 10 and Windows 11 versions |

Note

You might need to also configure the host for Enhanced session mode. For details, see [Use local resources on Hyper-V virtual machine with VMConnect](learn-more/use-local-resources-on-hyper-v-virtual-machine-with-vmconnect).

## Security

| Feature | Generation | Guest operating system |
| --- | --- | --- |
| Secure boot | 2 | **Linux**: Ubuntu 14.04 and later, SUSE Linux Enterprise Server 12 and later, Red Hat Enterprise Linux 7.0 and later, and CentOS 7.0 and later; **Windows**: All supported versions that can run on a generation 2 virtual machine |
| Shielded virtual machines | 2 | **Windows**: All supported versions that can run on a generation 2 virtual machine |

## Storage

| Feature | Generation | Guest operating system |
| --- | --- | --- |
| Shared virtual hard disks (VHDX only) | 1 and 2 | Windows Server 2012 and later |
| SMB3 | 1 and 2 | All that support SMB3 |
| Storage spaces direct | 2 | Windows Server 2016 and later |
| Virtual Fibre Channel | 1 and 2 | Windows Server 2012 and later |
| VHDX format | 1 and 2 | Any supported guest |