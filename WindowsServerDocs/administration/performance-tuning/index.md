---
layout: Conceptual
title: Windows Server 2022 Performance Tuning Guidelines | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Performance tuning guidelines for Windows Server 2022
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 6d673198-cf0c-5e77-9416-0f5e5e4d7f0e
document_version_independent_id: a689482c-674d-fcf2-0375-e8066d543973
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/performance-tuning/index.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/performance-tuning/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/performance-tuning/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: a6789457-563f-5a21-0b25-cddb9b93c842
---

# Windows Server 2022 Performance Tuning Guidelines | Microsoft Learn

When you run a server system in your organization, you might have business needs not met using default server settings. For example, you might need the lowest possible energy consumption, or the lowest possible latency, or the maximum possible throughput on your server. This guide provides a set of guidelines that you can use to tune the server settings in Windows Server 2022 and obtain incremental performance or energy efficiency gains, especially when the nature of the workload varies little over time.

It is important that your tuning changes consider the hardware, the workload, the power budgets, and the performance goals of your server. This guide describes each setting and its potential effect to help you make an informed decision about its relevance to your system, workload, performance, and energy usage goals.

Warning

Registry settings and tuning parameters changed significantly between versions of Windows Server. Be sure to use the latest tuning guidelines to avoid unexpected results.

## In this guide

This guide organizes performance and tuning guidance for Windows Server 2022 across three tuning categories:

| Server Hardware | Server Role | Server Subsystem |
| --- | --- | --- |
| [Hardware performance considerations](hardware/) | [Active Directory Servers](role/active-directory-server/) | [Cache and memory management](subsystem/cache-memory-management/) |
| [Hardware power considerations](hardware/power) | [File Servers](role/file-server/) | [Networking subsystem](../../networking/technologies/network-subsystem/net-sub-performance-top) |
|  | [Hyper-V Servers](role/hyper-v-server/) | [Storage Spaces Direct](/en-us/azure/azure-local/concepts/storage-spaces-direct-overview) |
|  | [Remote Desktop Services](role/remote-desktop/session-hosts) | [Software Defined Networking (SDN)](subsystem/software-defined-networking/) |
|  | [Web Servers](role/web-server/) |  |
|  | [Windows Server Containers](role/windows-server-container/) |  |

## Changes in this version

### Sections added

- [Software Defined Networking](subsystem/software-defined-networking/), including [HNV](subsystem/software-defined-networking/hnv-gateway-performance) and [SLB gateway configuration guidance](subsystem/software-defined-networking/slb-gateway-performance)
- [Storage Spaces Direct](/en-us/azure/azure-local/concepts/storage-spaces-direct-overview)
- [HTTP1.1 and HTTP2](role/web-server/http-performance)
- [Windows Server Containers](role/windows-server-container/)

### Sections changed

- Updates to [Active Directory guidance](role/active-directory-server/) section
- Updates to [File Server guidance](role/file-server/) section
- Updates to [Web Server guidance](role/web-server/) section
- Updates to [Hardware Power guidance](hardware/power) section
- Updates to [PowerShell tuning guidance](/en-us/powershell/scripting/dev-cross-plat/performance/script-authoring-considerations) section
- Significant updates to the [Hyper-V guidance](role/hyper-v-server/) section
- *Performance Tuning for Workloads removed*, pointers to relevant resources added to [Additional Tuning Resources article](additional-resources)
- *Removal of dedicated storage sections*, in favor of new [Storage Spaces Direct](/en-us/azure/azure-local/concepts/storage-spaces-direct-overview) section and canonical Technet content
- *Removal of dedicated networking section*, in favor of canonical Technet content