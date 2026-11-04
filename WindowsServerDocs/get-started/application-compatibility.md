---
layout: Conceptual
title: Microsoft server applications compatibility for Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/application-compatibility
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Learn about the compatibility of Microsoft server applications on Windows Server.
ms.topic: feature-availability
ms.author: roharwoo
author: robinharwood
ms.date: 2025-01-13T00:00:00.0000000Z
zone_pivot_groups: windows-os-version
locale: en-us
document_id: 3cae1d4d-7417-908f-11f6-0f00ceb5e6cb
document_version_independent_id: 3cae1d4d-7417-908f-11f6-0f00ceb5e6cb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/application-compatibility.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/application-compatibility
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/application-compatibility.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/dc29fde7-b949-4135-9273-ad8e4a53d516
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/25d6050c-71f5-4b48-8bc7-575debd6530a
platformId: bd5a175d-74e7-af52-e69f-ac540b4c636c
---

# Microsoft server applications compatibility for Windows Server | Microsoft Learn

We understand that application compatibility is one of the top reasons that customers choose Windows Server. Throughout the Windows Server development cycle, Microsoft regularly tests a large suite of Microsoft and non-Microsoft applications to ensure our products are compatible with as many applications as possible. These tests cover a wide range of non-Microsoft enterprise applications, including development tools, graphics tools, security tools, business office suites, storage management, antivirus, backup or recovery, and utilities.

The following table lists Microsoft server applications that support installation and functionality on Window Server. This information is for quick reference and isn't intended to replace the individual product specifications, requirements, announcements, or general communications of each individual server application. Refer to official documentation for each product to fully understand compatibility and options.

Tip

If you're a software vendor partner looking for more information on Windows Server compatibility with non-Microsoft applications, visit the [Commercial App Certification portal](https://commercialappcertification.microsoft.com/).

::: zone pivot="windows-server-2025"

| Product | Supported on Server Core | Supported on Server with Desktop Experience | Product Web Link |
| --- | --- | --- | --- |
| Configuration Manager (version 2409) | ✅² | ✅ | [Support for Windows Server 2025](/en-us/mem/configmgr/core/plan-design/changes/whats-new-in-version-2409#operating-system-support-added-for-windows-11-24h2-and-windows-server-2025) |
| Exchange Server | ✅ | ✅ | [Exchange Server supportability matrix](/en-us/exchange/plan-and-deploy/supportability-matrix) |
| Microsoft 365 Apps | ❌ | ✅ | [Windows and Office configuration support matrix](https://aka.ms/windows-office-support-matrix) |
| Project Server Subscription Edition | ✅ | ✅ | [Software requirements for Project Server Subscription Edition](/en-us/project/software-requirements-project-server-subscription-edition) |
| SharePoint Server Subscription Edition | ✅ | ✅ | [System requirements for SharePoint Server Subscription edition](/en-us/sharepoint/install/system-requirements-for-sharepoint-subscription-edition) |
| SQL Server 2019 | ✅¹ | ✅ | [Hardware and Software Requirements for Installing SQL Server 2019](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2019?view=sql-server-ver15&amp;preserve-view=true) |
| SQL Server 2022 | ✅¹ | ✅ | [Hardware and Software Requirements for Installing SQL Server 2022](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2022?view=sql-server-ver16&amp;preserve-view=true) |
| System Center Data Protection Manager | ✅¹ | ✅ | [Preparing your environment for System Center Data Protection Manager](/en-us/system-center/dpm/prepare-environment-for-dpm) |
| System Center Operations Manager | ✅¹ | ✅ | [System requirements for System Center Operations Manager](/en-us/system-center/scom/system-requirements) |
| System Center Virtual Machine Manager | ✅¹ | ✅ | [System requirements for System Center Virtual Machine Manager](/en-us/system-center/vmm/system-requirements) |

1. Might have limitations or require the [Server Core App Compatibility Feature on Demand (FOD)](server-core-app-compatibility-feature-on-demand). For more information, see specific product or Feature on Demand documentation.
2. Yes, as a managed client and distribution point but not as a site server.

::: zone-end

::: zone pivot="windows-server-2022"

| Product | Supported on Server Core | Supported on Server with Desktop Experience | Product Web Link |
| --- | --- | --- | --- |
| Azure DevOps Server 2020.1 | ✅¹ | ✅ | [Azure DevOps Server 2020.1 release notes](/en-us/azure/devops/server/release-notes/azuredevops2020u1?view=azure-devops&amp;preserve-view=true) |
| Configuration Manager (version 2107) | ✅² | ✅ | [Support for Windows Server 2022](/en-us/mem/configmgr/core/plan-design/changes/whats-new-in-version-2107#support-for-windows-server-2022-and-the-adk-for-windows-11) |
| Exchange Server 2019 CU12 and later | ✅ | ✅ | [Exchange Server supportability matrix](/en-us/exchange/plan-and-deploy/supportability-matrix) |
| Host Integration Server 2020 | ✅ | ✅ | [HIS 2020 - What's New, Release Notes, System Requirements, and Installation](/en-us/host-integration-server/install-and-config-guides/his-2020-what-s-new-release-notes-system-requirements-and-installation) |
| Microsoft 365 Apps | ❌ | ✅ | [Windows and Office configuration support matrix](https://aka.ms/windows-office-support-matrix) |
| Office Online Server | ❌ | ✅ | [Plan Office Online Server](/en-us/officeonlineserver/plan-office-online-server) |
| Project Server 2019 | ❌ | ✅ | [Software requirements for Project Server 2019 - Project Server](/en-us/project/software-requirements-for-project-server-2019) |
| Project Server Subscription Edition | ✅ | ✅ | [Software requirements for Project Server Subscription Edition](/en-us/project/software-requirements-project-server-subscription-edition) |
| SharePoint Server 2019 | ❌ | ✅ | [Hardware and software requirements for SharePoint Server 2019](/en-us/sharepoint/install/hardware-and-software-requirements-2019) |
| SharePoint Server Subscription Edition | ✅ | ✅ | [System requirements for SharePoint Server Subscription edition](/en-us/sharepoint/install/system-requirements-for-sharepoint-subscription-edition) |
| SQL Server 2017 | ✅¹ | ✅ | [Hardware and Software Requirements for Installing SQL Server 2017](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2017&amp;preserve-view=true) |
| SQL Server 2019 | ✅¹ | ✅ | [Hardware and Software Requirements for Installing SQL Server 2019](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2019?view=sql-server-ver15&amp;preserve-view=true) |
| SQL Server 2022 | ✅¹ | ✅ | [Hardware and Software Requirements for Installing SQL Server 2022](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2022?view=sql-server-ver16&amp;preserve-view=true) |
| System Center Data Protection Manager 2019 | ✅³ | ✅³ | [Preparing your environment for System Center Data Protection Manager](/en-us/system-center/dpm/prepare-environment-for-dpm?view=sc-dpm-2019&amp;preserve-view=true) |
| System Center Data Protection Manager 2022 | ✅¹ | ✅ | [Preparing your environment for System Center Data Protection Manager](/en-us/system-center/dpm/prepare-environment-for-dpm?view=sc-dpm-2022&amp;preserve-view=true) |
| System Center Operations Manager 2019 | ✅⁴ | ✅⁴ | [System requirements for System Center Operations Manager](/en-us/system-center/scom/system-requirements?view=sc-om-2019&amp;preserve-view=true) |
| System Center Operations Manager 2022 | ✅¹ | ✅ | [System requirements for System Center Operations Manager](/en-us/system-center/scom/system-requirements?view=sc-om-2022&amp;preserve-view=true) |
| System Center Virtual Machine Manager 2022 | ✅¹ | ✅ | [System requirements for System Center Virtual Machine Manager](/en-us/system-center/vmm/system-requirements?view=sc-vmm-2022&amp;preserve-view=true) |

1. Might have limitations or require the [Server Core App Compatibility Feature on Demand (FOD)](server-core-app-compatibility-feature-on-demand). For more information, see specific product or Feature on Demand documentation.
2. Yes, as a managed client and distribution point but not as a site server.
3. Yes as a backup workload but not as a Data Protection Manager server.
4. Yes as an agent but not as a Management Server.

::: zone-end

::: zone pivot="windows-server-2019"

| Product | Supported on Server Core | Supported on Server with Desktop Experience | Product Web Link |
| --- | --- | --- | --- |
| Azure DevOps Server 2019 | ✅¹ | ✅ | [Azure DevOps Server 2019](/en-us/azure/devops/server/requirements?view=azure-devops-2019&amp;preserve-view=true) |
| Azure DevOps Server 2020 | ✅¹ | ✅ | [Azure DevOps Server 2020](/en-us/azure/devops/server/requirements?view=azure-devops-2020&amp;preserve-view=true) |
| Configuration Manager (version 1806) | ✅² | ✅² | [What's new in version 1806 of Configuration Manager current branch](/en-us/configmgr/core/plan-design/changes/whats-new-in-version-1806) |
| Exchange Server 2019 | ✅ | ✅ | [Exchange Server supportability matrix](/en-us/exchange/plan-and-deploy/supportability-matrix) |
| Host Integration Server 2016, CU3 | ✅ | ✅ | [Host Integration Server system requirements](/en-us/host-integration-server/install-and-config-guides/system-requirements) |
| Office Online Server | ❌ | ✅ | [Plan Office Online Server](/en-us/officeonlineserver/plan-office-online-server) |
| Project Server 2016 | ❌ | ✅ | [Software requirements for Project Server 2016](/en-us/project/software-requirements-for-project-server-2016) |
| Project Server 2019 | ❌ | ✅ | [Software requirements for Project Server 2019](/en-us/project/software-requirements-for-project-server-2019) |
| Project Server Subscription Edition | ✅ | ✅ | [Software requirements for Project Server Subscription Edition](/en-us/project/software-requirements-project-server-subscription-edition) |
| SharePoint Server 2016 | ❌ | ✅ | [Hardware and software requirements for SharePoint Server 2016](/en-us/sharepoint/install/hardware-and-software-requirements) |
| SharePoint Server 2019 | ❌ | ✅ | [Hardware and software requirements for SharePoint Server 2019](/en-us/sharepoint/install/hardware-and-software-requirements-2019) |
| SharePoint Server Subscription Edition | ✅ | ✅ | [System requirements for SharePoint Server Subscription edition](/en-us/sharepoint/install/system-requirements-for-sharepoint-subscription-edition) |
| Skype for Business 2019 | ❌ | ✅ | [Install prerequisites for Skype for Business Server](/en-us/skypeforbusiness/deploy/install/install-prerequisites) |
| SQL Server 2014 | ✅¹ | ✅ | [Hardware and Software Requirements for Installing SQL Server 2014](/en-us/previous-versions/sql/2014/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2014&amp;preserve-view=true) |
| SQL Server 2016 | ✅¹ | ✅ | [Hardware and Software Requirements for Installing SQL Server 2016](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2016&amp;preserve-view=true) |
| SQL Server 2017 | ✅¹ | ✅ | [Hardware and Software Requirements for Installing SQL Server 2017](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2017&amp;preserve-view=true) |
| SQL Server 2019 | ✅¹ | ✅ | [Hardware and Software Requirements for Installing SQL Server 2019](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2019?view=sql-server-ver15&amp;preserve-view=true) |
| SQL Server 2022 | ✅¹ | ✅ | [Hardware and Software Requirements for Installing SQL Server 2022](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2022?view=sql-server-ver16&amp;preserve-view=true) |
| System Center Data Protection Manager 2019 | ❌ | ✅ | [Preparing your environment for System Center Data Protection Manager](/en-us/system-center/dpm/prepare-environment-for-dpm) |
| System Center Operations Manager 2019 | ✅¹ | ✅ | [System requirements for System Center Operations Manager](/en-us/system-center/scom/plan-system-requirements) |
| System Center Virtual Machine Manager 2019 | ✅¹ | ✅ | [System requirements for System Center Virtual Machine Manager](/en-us/system-center/vmm/system-requirements) |

1. Might have limitations or require the [Server Core App Compatibility Feature on Demand (FOD)](server-core-app-compatibility-feature-on-demand). For more information, see specific product or Feature on Demand documentation.
2. Yes, as a managed client and distribution point but not as a site server.

::: zone-end

::: zone pivot="windows-server-2016"

| Product | Product Web Link |
| --- | --- |
| BizTalk Server 2016 | [Microsoft BizTalk Server](https://www.microsoft.com/cloud-platform/biztalk) |
| Configuration Manager (version 1606) | [What's new in version 1606 of Configuration Manager](/en-us/mem/configmgr/core/plan-design/changes/whats-new-in-version-1606) |
| Exchange Server 2016 | [Exchange Server supportability matrix](/en-us/exchange/plan-and-deploy/supportability-matrix) |
| Host Integration Server 2016 | [What's New in HIS 2016](/en-us/host-integration-server/install-and-config-guides/what-s-new-in-his-2016) |
| Office Online Server | [Plan Office Online Server](/en-us/officeonlineserver/plan-office-online-server) |
| Project Server 2016 | [Software requirements for Project Server 2016](/en-us/project/software-requirements-for-project-server-2016) |
| Project Server 2019 | [Software requirements for Project Server 2019](/en-us/project/software-requirements-for-project-server-2019) |
| SharePoint Server 2016 | [Hardware and software requirements for SharePoint Server 2016](/en-us/SharePoint/install/hardware-and-software-requirements) |
| SharePoint Server 2019 | [Hardware and software requirements for SharePoint Server 2019](/en-us/sharepoint/install/hardware-and-software-requirements-2019) |
| Skype for Business Server 2015 | [How to install Skype for Business Server 2015 on Windows Server 2016](https://support.microsoft.com/help/4015888/how-to-install-skype-for-business-server-2015-on-windows-server-2016) |
| SQL Server 2012 | [Hardware and Software Requirements for Installing SQL Server 2012](/en-us/previous-versions/sql/sql-server-2012/ms143506%28v=sql.110%29) |
| SQL Server 2014 | [Hardware and Software Requirements for Installing SQL Server 2014](/en-us/previous-versions/sql/2014/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2014&amp;preserve-view=true) |
| SQL Server 2016 | [Hardware and Software Requirements for Installing SQL Server 2016](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2016&amp;preserve-view=true) |
| SQL Server 2017 | [Hardware and Software Requirements for Installing SQL Server 2017](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2017&amp;preserve-view=true) |
| SQL Server 2019 | [Hardware and Software Requirements for Installing SQL Server 2019](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2019?view=sql-server-ver15&amp;preserve-view=true) |
| SQL Server 2022 | [Hardware and Software Requirements for Installing SQL Server 2022](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2022?view=sql-server-ver16&amp;preserve-view=true) |
| System Center Virtual Machine Manager 2016 | [What's New in System Center](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2014&amp;preserve-view=true) |
| System Center Operations Manager 2016 | [What's New in System Center](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2014&amp;preserve-view=true) |
| System Center Data Protection Manager 2016 | [What's New in System Center](/en-us/sql/sql-server/install/hardware-and-software-requirements-for-installing-sql-server?view=sql-server-2014&amp;preserve-view=true) |
| Visual Studio Team Foundation Server 2017 | [Team Foundation Server 2017](https://www.visualstudio.com/news/releasenotes/tfs2017-relnotes) |

::: zone-end