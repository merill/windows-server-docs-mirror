---
layout: Conceptual
title: Supported Linux and FreeBSD virtual machines for Hyper-V on Windows Server and Windows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Lists the Linux and FreeBSD integration services and features included in each version.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-19T00:00:00.0000000Z
locale: en-us
document_id: 507cf3f3-b101-09e3-8df8-94a583b0e931
document_version_independent_id: 433623b7-c49d-8d57-00e1-065073b425e8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/supported-linux-and-freebsd-virtual-machines-for-hyper-v-on-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 93924a13-7864-1e93-45f5-516d14b7da3b
---

# Supported Linux and FreeBSD virtual machines for Hyper-V on Windows Server and Windows | Microsoft Learn

Hyper-V supports both emulated and Hyper-V-specific devices for Linux and FreeBSD virtual machines. When running with emulated devices, no additional software is required to be installed. However emulated devices do not provide high performance and cannot leverage the rich virtual machine management infrastructure that the Hyper-V technology offers. In order to make full use of all benefits that Hyper-V provides, it is best to use Hyper-V-specific devices for Linux and FreeBSD. The collection of drivers that are required to run Hyper-V-specific devices are known as Linux Integration Services (LIS) or FreeBSD Integration Services (BIS).

LIS has been added to the Linux kernel and is updated for new releases. But Linux distributions based on older kernels may not have the latest enhancements or fixes. Microsoft provides a download containing installable LIS drivers for some Linux installations based on these older kernels. Because distribution vendors include versions of Linux Integration Services, it is best to install the latest downloadable version of LIS, if applicable, for your installation.

For other Linux distributions LIS changes are regularly integrated into the operating system kernel and applications so no separate download or installation is required.

For older FreeBSD releases (before 10.0), Microsoft provides ports that contain the installable BIS drivers and corresponding daemons for FreeBSD virtual machines. For newer FreeBSD releases, BIS is built in to the FreeBSD operating system, and no separate download or installation is required except for a KVP ports download that is needed for FreeBSD 10.0.

Tip

- Download [Windows Server](https://www.microsoft.com/evalcenter/evaluate-windows-server-2022) from the Evaluation Center.

The goal of this content is to provide information that helps facilitate your Linux or FreeBSD deployment on Hyper-V. Specific details include:

- Linux distributions or FreeBSD releases that require the download and installation of LIS or BIS drivers.
- Linux distributions or FreeBSD releases that contain built-in LIS or BIS drivers.
- Feature distribution maps that indicate the features in major Linux distributions or FreeBSD releases.
- Known issues and workarounds for each distribution or release.
- Feature description for each LIS or BIS feature.