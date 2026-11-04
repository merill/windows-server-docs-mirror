---
layout: Conceptual
title: RDS - Build and deploy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-build-and-deploy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Steps to build a Remote Desktop deployment
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: install-set-up-deploy
author: robinharwood
locale: en-us
document_id: 3614e2b2-46f1-cb28-dc4e-166867f3709b
document_version_independent_id: ddaad536-5671-b8f3-d543-69f6ab464b11
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-build-and-deploy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-build-and-deploy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-build-and-deploy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: c57f0a5d-5e8d-99c3-24ef-e9a0c1b39bc0
---

# RDS - Build and deploy | Microsoft Learn

A Remote Desktop Services deployment is the infrastructure used to share apps and resources with your users. Depending on the experience you want to provide, you can make it as small or complex as you need. Remote Desktop deployments are easily scaled. You can increase and decrease Remote Desktop Web Access, Gateway, Connection Broker and Session Host servers at will. You can use Remote Desktop Connection Broker to distribute workloads. Active Directory based authentication provides a highly secure environment.

[Remote Desktop clients](clients/remote-desktop-clients) enable access from any Windows, Apple, or Android computer, tablet, or phone.

See [Remote Desktop Services architecture](desktop-hosting-logical-architecture) for a detailed discussion of the different pieces that work together to make up your Remote Desktop Services deployment.

Have an existing Remote Desktop deployment built on a previous version of Windows Server? Check out your options for moving to the latest version of Windows Server, where you can take advantage of new and better functionality around performance and scale:

- [Migrate your RDS deployment](migrate-rds-role-services)
- [Upgrade your RDS deployment](upgrade-to-rds)

Want to create a new Remote Desktop deployment? Use the following information to deploy Remote Desktop in Windows Server:

- [Deploy the Remote Desktop Services infrastructure](rds-deploy-infrastructure)
- [Create a session collection to hold the apps and resources you want to share](rds-create-collection)
- [License your RDS deployment](rds-client-access-license)
- Have your users install a [Remote Desktop client](clients/remote-desktop-clients) so they can access the apps and resources.
- Enable high availability by adding additional Connection Brokers and Session Hosts:
    - [Scale out an existing RDS collection with an RD Session Host farm](rds-scale-rdsh-farm)
    - [Add high availability to the RD Connection Broker infrastructure](rds-connection-broker-cluster)
    - [Add high availability to the RD Web and RD Gateway web front](rds-rdweb-gateway-ha)
    - [Deploy a two-node Storage Spaces Direct file system for UPD storage](rds-storage-spaces-direct-deployment)