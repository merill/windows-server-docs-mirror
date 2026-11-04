---
layout: Conceptual
title: Remote Desktop Services - Build anywhere | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-plan-build-anywhere
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Planning information to help you determine where to host your RDS deployment.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: 26f3db62-b335-df7d-cf27-5ed24e752411
document_version_independent_id: ab3c3d75-fef3-87e0-2070-cfb95caf3b5c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-plan-build-anywhere.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-plan-build-anywhere
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-plan-build-anywhere.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f9c5a1ec-b35e-b4f4-1eef-36f758b4c38b
---

# Remote Desktop Services - Build anywhere | Microsoft Learn

Deploy on-premises, in the cloud, or a hybrid of the two. Modify your deployment as your business needs change.

Regardless of where you are, the underlying [architecture](desktop-hosting-logical-architecture) of the Remote Desktop Services environment remains the same:

- You still must have an internet-facing server to utilize RD Web Access and RD Gateway for external users
- You still must have an Active Directory and--for highly available environments--a SQL database to house user and Remote Desktop properties
- You still must have communication access between the RD infrastructure roles (RD Connection Broker, RD Gateway, RD Licensing, and RD Web Access) and the end RDSH or RDVH hosts to be able to connect end-users to their desktops or applications.

This flexibility allows you to get the best of both worlds:

- The simplicity and pay-as-you-go methods associated with the cloud and the online world.
- The familiarity and hassle-free way of leveraging heavy resources that already exist on-premises.

For additional information, look at how to [build and deploy your Remote Desktop Services deployment](rds-build-and-deploy).