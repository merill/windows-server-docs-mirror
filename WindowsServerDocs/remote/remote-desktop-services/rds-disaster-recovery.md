---
layout: Conceptual
title: Protect your RDS deployment - Disaster recovery | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-disaster-recovery
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn about your disaster recovery options for Remote Desktop Services
ms.topic: solution-overview
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: f98667e2-b404-ced9-457a-014560b5cded
document_version_independent_id: a4ca9a59-5d0c-19e0-ecc7-1bd2d4127e4e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-disaster-recovery.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-disaster-recovery
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-disaster-recovery.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d15e3a29-5284-981d-8dd4-d06c8789a8f8
---

# Protect your RDS deployment - Disaster recovery | Microsoft Learn

When you deploy Remote Desktop Services into your environment, it becomes a critical part of your infrastructure, particularly the apps and resources that you share with users. If the RDS deployment goes down due to anything from a network failure to a natural disaster, users can't access those apps and resources, and your business is negatively impacted. To avoid this, you can configure a disaster recovery solution that allows you to failover your deployment - if your RDS deployment is unavailable, for whatever reason, there is a backup available to automatically take over.

To keep your RDS deployment running in the case of a single component or machine going down, we recommend configuring your RDS deployment for high availability. You can do this by setting up an [RDSH farm](rds-scale-rdsh-farm) and ensuring your [Connection Brokers are clustered for high availability](rds-connection-broker-cluster).

The disaster recovery solutions we recommend here are to protect your deployment from catastrophic disaster - something that takes down your entire RDS deployment (including redundant roles configured for high availability). If such a disaster hits, having a disaster recovery solution built into your deployment will allow you to failover the entire deployment and quickly get apps and resources up and running for your users.

Use the following information to deploy disaster recovery solutions in RDS:

- [Leverage multiple Azure data centers to ensure users can access your RDS deployment, even if one Azure data center goes down (geo-redundancy)](rds-multi-datacenter-deployment)
- [Deploy Azure Site Recovery to provide failover for RDS components in site-to-site or site-to-Azure failovers](rds-disaster-recovery-with-azure)