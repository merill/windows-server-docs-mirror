---
layout: Conceptual
title: Determine Your AD FS Deployment Topology | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/determine-your-ad-fs-deployment-topology
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Determine Your AD FS Deployment Topology'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 62721bd3-925d-08eb-a27c-49cbcbb4a253
document_version_independent_id: d03cfee1-ac41-0c24-f96b-cd60d1897983
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Determine-Your-AD-FS-Deployment-Topology.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/determine-your-ad-fs-deployment-topology
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Determine-Your-AD-FS-Deployment-Topology.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9cb080d5-9135-03e3-0f68-70ed417ce530
---

# Determine Your AD FS Deployment Topology | Microsoft Learn

The first step in planning a deployment of Active Directory Federation Services (AD FS) is to determine the right deployment topology to meet the single sign-on (SSO) needs of your organization. The topics in this section describe the various deployment topologies that you can use with AD FS. They also describe the benefits and limitations associated with each deployment topology so that you can select the most appropriate topology for your specific business needs.

Before you read this deployment topology topic, we recommend that you first complete the tasks in the order shown in the following table.

| Recommended task | Description | Reference |
| --- | --- | --- |
| Review how AD FS data is stored and replicated to other federation servers in a federation server farm. | Understand the purpose of and the replication methods that can be used for the underlying data that is stored in the AD FS configuration database. This topic introduces the concepts of the configuration database and describes the two database types: Windows Internal Database (WID) and Microsoft SQL Server. | [The Role of the AD FS Configuration Database](../technical-reference/the-role-of-the-ad-fs-configuration-database) |
| Select the type of AD FS configuration database that you will deploy in your organization. | Review the various benefits and limitations that are associated with using either WID or SQL Server as the AD FS configuration database, along with the various application scenarios that they support. | [AD FS Deployment Topology Considerations](ad-fs-deployment-topology-considerations) |

Note

To implement basic redundancy, load balancing, and the option to scale the Federation Service (if required), we recommend that you deploy at least two federation servers per federation server farm for all production environments, regardless of the type of database that you will use.

When you have reviewed the content in the previous table, proceed to the following topics in this section:

- [Stand-Alone Federation Server Using WID](stand-alone-federation-server-using-wid)
- [Federation Server Farm Using WID](federation-server-farm-using-wid-2012)
- [Federation Server Farm Using WID and Proxies](federation-server-farm-using-wid-and-proxies-2012)
- [Federation Server Farm Using SQL Server](federation-server-farm-using-sql-server-2012)

After you finish selecting your AD FS deployment topology, we recommend that you review the topic [Planning for AD FS Server Capacity](planning-for-ad-fs-server-capacity) to determine the recommended number of servers that you will need to deploy to support this topology.