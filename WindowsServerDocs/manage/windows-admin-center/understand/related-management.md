---
layout: Conceptual
title: Windows Admin Center related management solutions | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/understand/related-management
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: How Windows Admin Center compares with and complements other Microsoft monitoring and management solutions/products (Project Honolulu)
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 1aee2f82-9466-d90e-d925-50a404dc8f5b
document_version_independent_id: ba2eb7ec-e3f5-705b-b1d3-ed8744e925f6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/understand/related-management.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/understand/related-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/understand/related-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1ff955b5-46e4-bbdf-3de9-0a89d74611c7
---

# Windows Admin Center related management solutions | Microsoft Learn

[Windows Admin Center](../overview) is the evolution of traditional in-box server management tools for situations where you might have used Remote Desktop (RDP) to connect to a server for troubleshooting or configuration. It's not intended to replace other existing Microsoft management solutions; rather it complements these solutions, as described below.

## Remote Server Administration Tools (RSAT)

[Remote Server Administration Tools (RSAT)](../../../remote/remote-server-administration-tools) is a collection of GUI and PowerShell tools to manage optional roles and features in Windows Server. RSAT has many capabilities that Windows Admin Center doesn't have. We may add some of the most commonly used tools in RSAT to Windows Admin Center in the future. Any new Windows Server role or feature that requires a GUI for management will be in Windows Admin Center.

## Intune

[Intune](https://www.microsoft.com/cloud-platform/microsoft-intune) is a cloud-based enterprise mobility management service that lets you manage iOS, Android, Windows, and macOS devices, based on a set of policies. Intune focuses on enabling you to secure company information by controlling how your workforce accesses and shares information. In contrast, Windows Admin Center is not policy-driven, but enables ad-hoc management of Windows 10 and Windows Server systems, using remote PowerShell and WMI over WinRM.

## Azure Stack

[Azure Stack](https://azure.microsoft.com/overview/azure-stack/) is a hybrid cloud platform that lets you deliver Azure services from your data center. Azure Stack is managed using PowerShell or the administrator portal, which is similar to the traditional Azure portal used to access and manage traditional Azure services. Windows Admin Center isn't intended to manage the Azure Stack infrastructure, but you can use it to [manage Azure IaaS virtual machines](../azure/manage-azure-vms) (running Windows Server 2016, Windows Server 2012 R2, or Windows Server 2012) or troubleshoot individual physical servers deployed in your Azure Stack environment.

## System Center

[System Center](https://www.microsoft.com/cloud-platform/system-center) is an on-premises data center management solution for deployment, configuration, management, monitoring your entire data center. System Center lets you see the status of all the systems in your environment, while Windows Admin Center lets you drill down into a specific server to manage or troubleshoot it with more granular tools.

| Windows Admin Center | System Center |
| --- | --- |
| **Reimagined “in-box” platform & tools** | **Datacenter management & monitoring** |
| Included with Windows Server license – **no additional cost**, just like MMC and other traditional in-box tools | **Comprehensive** suite of solutions for additional value across your environment and platforms |
| **Lightweight**, browser-based remote management of Windows Server instances, **anywhere**; alternative to RDP | Manage & monitor **heterogeneous** systems **at scale**, including Hyper-V, VMware, and Linux |
| **Deep** single-server & single-cluster drill-down for troubleshooting, configuration & maintenance | Infrastructure provisioning; automation and self-service; infrastructure and workload monitoring **breadth** |
| Optimized management of **individual** 2–4 node **HCI** clusters, integrating Hyper-V, Storage Spaces Direct, and SDN | Deploy & manage Hyper-V, Windows Server clusters at **datacenter scale** from **bare metal** with SCVMM |
| **Monitoring on HCI** only; cluster health service stores history. Extensible platform for 1st and 3rd party **admin tool extensions** | **Extensible** & **scalable monitoring** platform in SCOM, with alerting, notifications, third-party workload monitoring; SQL for history |
| Easiest bridge to **hybrid**; onboard and use a variety of Azure services for data protection, replication, updates and more | **Built-in** data protection, replication, updates (DPM/VMM/SCCM). Hybrid integration with Log Analytics and Service Map |
| **Lights up platform features** of Windows Server: Storage Migration Service, Storage Replica, System Insights, etc. | **Additional platforms**: Automation in Orchestrator/SMA.Integrations with SCSM & other service management tools |

#### Each delivers targeted value independently; **better together** with complementary capabilities.