---
layout: Conceptual
title: Windows Admin Center overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn about Windows Admin Center and choose between Administration Mode for general administration and Virtualization Mode for virtualization infrastructure.
ms.topic: overview
author: davannaw-msft
ms.author: dawhite
ms.date: 2024-08-22T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: bd448b3c-456e-bd11-efb5-278296801fc0
document_version_independent_id: f82f9906-69aa-fc5b-e479-84b42b6c716f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: a3fb5794-c7ad-b0fb-dad4-28a01a432ab3
---

# Windows Admin Center overview | Microsoft Learn

Windows Admin Center is a browser-based management product for Windows Server infrastructure running in physical, virtual, on-premises, Azure, or hosted environments at no extra cost. It provides two management experiences: Administration Mode and Virtualization Mode.

To find out what's new, see [Release history](support/release-history).

## Choose a Windows Admin Center experience

Administration Mode and Virtualization Mode are part of the same Windows Admin Center product, but they serve different management scenarios. They're independent experiences that you install on separate systems, not modes that you switch between in a single deployment.

| Experience | Choose this experience when you need to |
| --- | --- |
| **Administration Mode** | Perform general administration and troubleshooting for individual servers and clusters. This experience provides tools for areas such as events, certificates, devices, networking, registry, roles and features, storage, and updates. |
| **Virtualization Mode** | Centrally manage virtualization infrastructure across large-scale, distributed Hyper-V environments. This experience provides resource-focused views and parallel operations for hosts, clusters, virtual machines, storage, and networking. |

You can use both experiences in the same environment. To compare their architecture, scale, and capabilities, see [What is Windows Admin Center Virtualization Mode?](virtualization-mode-overview#operational-modes)

## Download now

**Download**[Windows Admin Center](https://www.microsoft.com/evalcenter/download-windows-admin-center) from the Microsoft Evaluation Center.

For help installing Administration Mode, see [Install Windows Admin Center](deploy/install). For help installing Virtualization Mode, see [Install Windows Admin Center Virtualization Mode](install-virtualization-mode). For tips on getting started, see [Get started](use/get-started).

You can update non-preview versions of Windows Admin Center by using Microsoft Update or by manually downloading and installing Windows Admin Center. Each non-preview version is supported until 30 days after the next non-preview version is released. For more information, see the [Windows Admin Center support policy](support/).

## Windows Admin Center scenarios

Here are a few things you can use Windows Admin Center for:

- **Simplify server management**: Manage your servers and clusters with modernized versions of familiar tools such as Server Manager. Install in under five minutes and manage servers in your environment immediately, no extra configuration required. For details, see [What is Windows Admin Center?](understand/what-is)
- **Work with hybrid solutions**: Integration with Azure helps you optionally connect your on-premises servers with relevant cloud services. For details, see [Azure hybrid services](azure/).
- **Manage virtualization infrastructure**: Use Administration Mode to deploy and manage Windows Server hyperconverged clusters. For more information, see [Manage HCI](use/manage-hyper-converged). Use Virtualization Mode to centrally manage large-scale, distributed Hyper-V resources. For Azure Local management, see the [Azure Local documentation](/en-us/azure/azure-local/overview).

Here's a video to give you an overview, followed by a poster giving more details:

[![Diagram that gives an overview of the Windows Admin Center.](media/wac1910-poster-thumb-small.png)](media/wac1910-poster-thumb-small.png#lightbox)

## Windows Admin Center documentation at a glance

| Understand | Plan |
| --- | --- |
| - [What is Windows Admin Center?](understand/what-is) - [What is Windows Admin Center Virtualization Mode?](virtualization-mode-overview) - [Frequently asked questions](understand/faq) - [Case studies](understand/case-studies) - [Related management products](understand/related-management) | - [What type of installation is right for you?](plan/installation-options) - [User access options](plan/user-access-options) |

| Deploy | Configure |
| --- | --- |
| - [Prepare your environment](deploy/prepare-environment) - [Install Windows Admin Center](deploy/install) - [Enable high availability](deploy/high-availability) | - [Windows Admin Center settings](configure/settings) - [User access control and permissions](configure/user-access-control) - [Shared connections](configure/shared-connections) - [Extensions](configure/using-extensions) - [Automate with PowerShell](configure/use-powershell) |

| Use | Connect to Azure |
| --- | --- |
| - [Launch & add connections](use/get-started) - [Manage servers](use/manage-servers) - [Deploy hyperconverged infrastructure](use/deploy-hyperconverged-infrastructure) - [Manage hyperconverged infrastructure](use/manage-hyper-converged) - [Manage failover clusters](use/manage-failover-clusters) - [Manage virtual machines](use/manage-virtual-machines) - [Logging](use/logging) | - [Azure hybrid services](azure/) - [Connect Windows Admin Center to Azure](azure/azure-integration) - [Deploy Windows Admin Center in Azure](azure/deploy-wac-in-azure) - [Manage Azure VMs with Windows Admin Center](azure/manage-azure-vms) |

| Windows Admin Center in Azure | Support |
| --- | --- |
| - [Manage a Windows Server IaaS VMs](azure/manage-vm) - [Manage Azure Arc-enabled Servers (preview)](azure/manage-arc-hybrid-machines) - [Manage Azure Local clusters (preview)](azure/manage-hci-clusters) | - [Release history](support/release-history) - [Support policy](support/) - [Common troubleshooting steps](support/troubleshooting) - [Known issues](support/known-issues) |

| Extend |
| --- |
| - [Overview of extensions](extend/extensibility-overview)- [Understanding extensions](extend/understand-extensions)- [Develop an extension](extend/developing-extensions)- [Guides](extend/guides)- [Publishing extensions](extend/publish-extensions) |

## See how customers benefit from Windows Admin Center

- "[Windows Admin Center] has decreased our time/effort in managing the management system by over 75%."

    *- Rand Morimoto, President, Convergent Computing*
- "Thanks to [Windows Admin Center], we can manage our customers remotely from HTML5 portal without problem and with the full integration with Microsoft Entra ID, we're able to increase the security thanks to the multifactor authentication."

    *- Silvio Di Benedetto, Founder and Senior Consultant, Inside Technologies*
- "We have been able to deploy [Server Core] SKUs in a more effective way, improving resource efficiency, security, and automation while still achieving a good degree of productivity and reducing errors that can happen when relying on scripting only."

    *- Guglielmo Mengora, Founder and CEO, VaiSulWeb*
- "With [Windows Admin Center] customers especially in the SMB market now have an easy to use tool to manage their internal infrastructure. This minimizes administrative efforts and saves a lot of time. And the best of it: there are no additional license fees for [Windows Admin Center]!"

    *- Helmut Otto, Managing Director, SecureGUARD*

To read more about companies using Windows Admin Center in their production environments, see [Windows Admin Center Case Studies](understand/case-studies).

## Related Windows Admin Center management products

Windows Admin Center is designed for managing a single server or cluster. It complements but doesn't replace existing Microsoft monitoring and management solutions, such as Remote Server Administration Tools (RSAT), System Center, Intune, or Azure Stack.

To learn how Windows Admin Center complements other Microsoft management solutions, see [Windows Admin Center and related management solutions from Microsoft](understand/related-management).

## Stay updated on Windows Admin Center

- [Follow us on X (formerly Twitter)](https://twitter.com/servermgmt)
- [Windows Admin Center blog](https://aka.ms/wacblog)