---
layout: Conceptual
title: Planning for AD FS Server Capacity | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/planning-for-ad-fs-server-capacity
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Planning for AD FS Server Capacity'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: ae5bcfbc-5131-51d0-33e4-f132b538916d
document_version_independent_id: 522021ff-3540-72df-5371-39cfaf92beff
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Planning-for-AD-FS-Server-Capacity.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/planning-for-ad-fs-server-capacity
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Planning-for-AD-FS-Server-Capacity.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f9cf537e-3e5a-4f31-a8e2-d06c28985eda
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b0200c40-0bea-4a73-a79b-8c68e19d3d16
platformId: 1f88b36b-0a3b-1571-7350-708e9e45498e
---

# Planning for AD FS Server Capacity | Microsoft Learn

Note

The content provided in this topic does not reflect actual testing that was performed on servers running Windows Server 2012 . This topic will be updated once the required testing has been performed.

Capacity planning for Active Directory Federation Services (AD FS) is the process of forecasting peak usage periods for your Federation Service and planning or scaling-up your AD FS server deployment to meet those load requirements.

This section describes deployment guidelines for both the federation server and federation server proxy roles and is based on lab testing that was performed by the AD FS product team at Microsoft. The purpose of this content is to help you:

- Closely estimate the hardware needs for your organization's specific AD FS deployment, such as the number of AD FS servers.
- Accurately project the expected peak usage for sign-in requests, plan for growth, and ensure that your AD FS deployment is capable of handling that expected peak usage.

Before you proceed with reading this capacity planning content, we recommend that you first complete the tasks in the order shown in the following two tables. In the first table, we provide links to recommended tasks that will help provide relevant context for this capacity planning discussion.

| Recommended task | Description | Reference |
| --- | --- | --- |
| Understand the requirements for deploying AD FS federation servers and federation server proxies | Review important hardware and software requirements necessary for deploying federation server and federation server proxies. | [Appendix A: Reviewing AD FS Requirements](appendix-a--reviewing-ad-fs-requirements) |
| Select the type of AD FS configuration database that you will deploy in your organization | Before you can begin using capacity planning data in this section, you first have to determine which AD FS configuration database type you will deploy, either Windows Internal Database (WID) or a Structured Query Language (SQL) database. | [The Role of the AD FS Configuration Database](../technical-reference/the-role-of-the-ad-fs-configuration-database);<br>[AD FS Deployment Topology Considerations](ad-fs-deployment-topology-considerations) |
| Determine the type of topology layout to use with your new AD FS configuration database selection | Once you have decided on the type of AD FS configuration database to use in your deployment, you will need to consider which deployment topology most closely matches where you will need to place federation servers and federation server proxies within your production environment. | [Determine Your AD FS Deployment Topology](determine-your-ad-fs-deployment-topology) |
| Understand key AD FS–related capacity planning terms | Review the definitions of common capacity planning terms that are used throughout the AD FS capacity planning discussion. | See the section titled [AD FS capacity planning terms](planning-for-ad-fs-server-capacity#bk_terms) in this topic |

Once you have reviewed the content in the previous table, you can now complete the prerequisite tasks in the next table.

| Prerequisite task | Description | Reference |
| --- | --- | --- |
| Download the AD FS Capacity Planning Sizing Spreadsheet | The AD FS Capacity Planning Sizing spreadsheet can help you to determine the number of federation servers required for an AD FS federation server farm deployment. Instructions for how to use this spreadsheet are available in the link provided below for the next task. | [AD FS Capacity Planning Spreadsheet](https://adfsdocs.blob.core.windows.net/adfs/ADFSCapacityPlanning.xlsx) |
| Gather data about the number of users who will require single sign-on (SSO) access to the target claims-aware application and the expected peak usage periods associated with this access | This user data you collect will be used for the input values required within the context of the AD FS Capacity Planning Sizing Spreadsheet. | [Estimate the number of federation servers for your organization](planning-for-federation-server-capacity#bk_estimatefs) |
| AD FS Capacity Planning Spreadsheet for Windows Server 2016 | Updated Planning worksheet for Windows Server 2016 | [AD FS Windows Server 2016 Capacity Planning](https://adfsdocs.blob.core.windows.net/adfs/ADFSCapacity2016.xlsx) |

## AD FS capacity planning terms

The following table describes important terms that are used often in this capacity planning section of the AD FS Design Guide. For a more complete list of AD FS terms, see [Understanding Key AD FS Concepts](../technical-reference/understanding-key-ad-fs-concepts).

| Term | Definition |
| --- | --- |
| Concurrent users | The estimated number of users that are expected to submit requests to the service within a given period of time, usually a peak activity period. |
| Active users | The approximate average number of users that are active on a system, but not necessarily submitting requests, during a given period of time. |
| Defined users | A theoretical maximum user count, usually based on the number of users who have defined accounts in the system. |
| Requests per second | The number of requests either submitted by clients (when talking about the load on a system) or processed by servers (when talking about server throughput) in a second. This metric is used in planning server processor and memory capacity. |
| Target server responsiveness and utilization | Success metrics that bound the acceptable server performance range. Generally, if responsiveness goes below or utilization goes above the target, the system is considered to be overloaded and more capacity is required. |
| Windows Internal Database (WID) | The default AD FS configuration database that can be used as an alternative to SQL Server in certain AD FS deployments. |

## Configuration environment used during AD FS testing

This section describes the configuration environment that the AD FS product team used to perform its tests. The team used the following computer hardware, software, and network configuration to gather performance and scalability data in tests of the federation server:

- Dual Quad Core 2.27 gigahertz (GHz) (8 cores)
- 16-GB RAM
- Windows Server 2008 R2, Enterprise Edition
- Gigabit Network

Note

Although 16 GB's of RAM was used on the federation server during testing, a more moderate memory size, such as 4 GB's of RAM per federation server can be used for most AD FS deployments. The recommendations that are provided in this AD FS Capacity Planning content along with the results provided by the AD FS Capacity Planning Spreadsheet are based on assumptions that each federation server will use approximately 4GB's of RAM for most AD FS production environments.

The product team used the following configuration to gather performance and scalability data for the federation server proxy testing:

- Dual Quad Core 2.24 GHz (4 cores)
- 4-GB RAM
- Windows Server 2008 R2, Enterprise Edition
- Gigabit Network

Note

Capacity recommendations for AD FS servers can vary considerably, depending on the specifications you choose for the hardware and network configuration to be used in a given environment. As a point of reference, the sizing guidance provided in this content is based on a utilization target of 80 percent on the computers mentioned earlier.

## Measure AD FS server capacity

Typically, the hardware components that affect server performance and scalability are the CPU, memory, the disk, and network adapters. Fortunately, each of the AD FS components requires very little demand on memory and disk space. Network connectivity is an obvious requirement. Therefore, load tests that are performed on federation servers and federation server proxies concentrate on two primary areas for measuring server capacity:

- **Peak AD FS requests per second:** The number of sign-in requests that are processed per second on federation servers. This measurement can help you determine how many simultaneous users can sign in to a given server. You can use this measurement in conjunction with the CPU consumption measurement to understand this measurement's effect on performance.
- **CPU consumption:** The percentage by which CPU capacity is measured. This measurement can help you determine the overall CPU load that occurred based on the number of incoming sign-in requests per second.

## Continue reading more about AD FS capacity planning

After you have completed the prerequisite tasks and have become familiar with related terms and hardware requirements, you can use the following additional capacity planning content to help you determine the recommended number of AD FS servers required for your deployment:

- [Planning for Federation Server Capacity](planning-for-federation-server-capacity)
- [Planning for Federation Server Proxy Capacity](planning-for-federation-server-proxy-capacity)