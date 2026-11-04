---
layout: Conceptual
title: Remote Desktop Services - High availability | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-plan-high-availability
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Planning information about setting up a highly available RDS deployment.
ms.topic: best-practice
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: 60723f7e-747c-1b5c-ad16-7b2382dfe6d0
document_version_independent_id: fba257cf-e827-bf67-4af1-b4676a3a095a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-plan-high-availability.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-plan-high-availability
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-plan-high-availability.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 80804736-d7a4-4e19-5197-1da1dcc29d70
---

# Remote Desktop Services - High availability | Microsoft Learn

Failures and throttling are unavoidable in large-scale systems. It's simple to set up Remote Desktop infrastructure roles to support high availability and allow end users to connect seamlessly, every time.

In Remote Desktop Services, the following items represent the Remote Desktop infrastructure roles, with their respective guidance to establish high availability:

- [Remote Desktop Connection Broker](rds-connection-broker-cluster)
- [Remote Desktop Gateway](rds-rdweb-gateway-ha)
- [Remote Desktop Licensing](rds-client-access-license)
- [Remote Desktop Web Access](rds-rdweb-gateway-ha)

High availability is established by duplicating each of the roles services on a second machines. In Azure, you can receive a guaranteed uptime by placing the set of the two virtual machines (hosting the same role) in an availability sets.

Along with availability sets, you can now leverage the power of Azure SQL Database and its Azure-backed SLA to ensure that you always have connection information and can redirect users to their desktops and applications.

For best practices on creating your RDS environment, please see the [desktop hosting architecture](desktop-hosting-reference-architecture).