---
layout: Conceptual
title: Extensions for Windows Admin Center | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/extensibility-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Extensions for Windows Admin Center SDK (Project Honolulu)
ms.topic: concept-article
author: davannaw-msft
ms.author: dawhite
ms.date: 2018-09-17T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 0b0db7e5-6847-2e6a-9de3-e894561928ff
document_version_independent_id: a2855cd8-f527-93b7-47c8-17a8df2d859a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/extensibility-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/extensibility-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/extensibility-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 870872f6-0d1e-288f-45b6-df95dbb13c27
---

# Extensions for Windows Admin Center | Microsoft Learn

Windows Admin Center is built as an extensible platform to enable partners and developers to leverage existing capabilities within Windows Admin Center, seamlessly integrate with other IT administration products and solutions, and provide extra value to customers. Each solution and tool in Windows Admin Center is built as an extension using the same extensibility features available to partners and developers, so you can build powerful tools just like the ones available in Windows Admin Center today.

Windows Admin Center extensions are built using modern web technologies including HTML5, CSS, Angular, TypeScript and jQuery, and can manage target servers via PowerShell or WMI. You can also manage target servers, services, or devices over different protocols such as REST by building a Windows Admin Center gateway plugin.

## Why you should consider developing an extension for Windows Admin Center

Here's the value you can bring to your product and customers by developing extensions for Windows Admin Center:

- **Integrate with Windows Admin Center tools:** Integrate your products and services with server and cluster management tools in Windows Admin Center and deliver unified and seamless, end-to-end monitoring, management, troubleshooting experiences to your customers.
- **Leverage platform security, identity and management capabilities:** Enable Microsoft Entra ID support, multi-factor authentication, Role-Based Access Control (RBAC), logging, and auditing for your product and services by leveraging Windows Admin Center platform capabilities to meet the complex requirements of today's IT organizations.
- **Develop using the latest web technologies:** Quickly build stunning user experiences using modern web technologies including HTML5, CSS, Angular, TypeScript and jQuery, and rich, powerful UI controls included in the Windows Admin Center SDK.
- **Extend product outreach:** Become a part of the Windows Admin Center ecosystem with outreach to our expanding customer base.

## Start developing with the Windows Admin Center SDK

Getting started with Windows Admin Center development is easy! Sample code can be found for [tool](develop-tool), [solution](develop-solution), and [gateway plugin](develop-gateway-plugin) extension types in our SDK documentation. There you will use the Windows Admin Center SDK to build a new extension project, then follow the individual guides to customize your project to meet your needs.

We've made a Windows Admin Center [SDK design toolkit](https://github.com/Microsoft/windows-admin-center-sdk/blob/master/WindowsAdminCenterDesignToolkit.zip) available to help you rapidly mock up extensions in PowerPoint using Windows Admin Center styles, controls, and page templates. See what your extension can look like in Windows Admin Center before you start coding!

We also have sample code hosted on GitHub: [Developer Tools](https://aka.ms/wacsdk) is a sample solution extension containing a rich collection of controls that you can browse and use in your own extension. Developer Tools is a fully functioning extension that can be side-loaded into Windows Admin Center in Developer Mode.

See the topics below to learn more about the SDK and get started:

- [Understand how extensions work](understand-extensions)
- [Develop an extension](developing-extensions)
- [Guides](guides)
- [Publish your extension](publish-extensions)

## Partner Spotlight

See the amazing value our partners have started to bring to the Windows Admin Center ecosystem and try these extensions out today. Learn more on [how to install extensions](../configure/using-extensions) from Windows Admin Center.

### BiitOps

The BiitOps Changes extension provides change tracking for hardware, software, and configuration settings on your Windows Server physical/virtual machines. The BiitOps Changes extension will show precisely what is new, what has changed and what has been deleted in a single-pane-of-glass to help track issues related to compliance, reliability and security. [Learn more about the BiitOps Changes extension](case-studies/biitops).

![BiitOps extension](../media/extensibility-overview/biitops-1.png)

### DataON

The DataON MUST extension brings monitoring, management, and end-to-end insight into DataON's hyper-converged infrastructure and storage systems based on Windows Server. The MUST extension adds unique value such as historical data reporting, disk mapping, system alerts and SAN-like call home service, complementing the Windows Admin Center server and hyper-converged infrastructure management capabilities, through a seamless, unified experience. [Learn more about DataON's MUST extension and their development experience](case-studies/dataon).

![DataON MUST extension](../media/extensibility-overview/dataon-must-extension.png)

### Fujitsu

Fujitsu's ServerView Health and RAID Health extensions for Windows Admin Center provide in-depth monitoring and management of critical hardware components such as processors, memory, power, and storage subsystems for Fujitsu PRIMERGY servers. By utilizing the Windows Admin Center UX design patterns and UI controls, Fujitsu has brought us a huge step towards our vision of end-to-end insight into server roles and services, to operating system, and to hardware management through the Windows Admin Center platform. [Learn more about Fujitsu's extensions and their development experience](case-studies/fujitsu).

![Fujitsu ServerView extension](../media/extensibility-overview/fujitsu-serverview-extension.png)

### Lenovo

The Lenovo XClarity Integrator extension takes hardware management to the next level by seamlessly integrating into various experiences within Windows Admin Center. The XClarity Integrator solution provides a high-level view of all your Lenovo servers, and different tool extensions provide hardware details whether you are connected to a single server, failover cluster, or hyper-converged cluster. [Learn more about the Lenovo XClarity Integrator extension](case-studies/lenovo).

![Lenovo extension](../media/extensibility-overview/lenovo-extension.png)

### Pure Storage

Pure Storage provides enterprise, all-flash data storage solutions that deliver data-centric architecture to accelerate your business for a competitive advantage. The Pure Storage extension for Windows Admin Center provides a single-pane view into Pure FlashArray products and empowers users to conduct monitoring tasks, view real-time performance metrics, and manage storage volumes and initiators through a single UI experience. [Learn more about Pure's extensions and their development experience](case-studies/purestorage).

![Pure Storage extension](../media/extensibility-overview/purestorage-extension.png)

### QCT

The QCT Management Suite extension complements Windows Admin Center by providing physical server monitoring and management for QCT Azure Local certified systems. The QCT Management Suite extension displays server hardware information, and provides an intuitive wizard UI to help replace physical disks efficiently, hardware event log tools, and S.M.A.R.T. based predictive disk management. [Learn more about the QCT Management Suite extension](case-studies/qct).

![QCT extension](../media/extensibility-overview/qct-extension.png)