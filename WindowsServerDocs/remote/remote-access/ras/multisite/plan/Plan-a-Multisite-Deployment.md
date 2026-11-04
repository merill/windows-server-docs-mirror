---
layout: Conceptual
title: Plan a Multisite Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/multisite/plan/plan-a-multisite-deployment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn about the planning steps required in order to deploy  Windows Server 2016 or  Windows Server 2012  Remote Access in a multisite configuration.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: fcdbdecb-73ea-540b-d306-d919954d7741
document_version_independent_id: ce5cdbf2-a6d0-804b-8cfa-dcfd9138e6d4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/multisite/plan/Plan-a-Multisite-Deployment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/multisite/plan/plan-a-multisite-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/multisite/plan/Plan-a-Multisite-Deployment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f8cb3efe-2bc2-aef2-e7a0-9a8b9135a48e
---

# Plan a Multisite Deployment | Microsoft Learn

Windows Server 2016, Windows Server 2012 combine DirectAccess and Routing and Remote Access Service (RRAS) VPN into a single Remote Access role. This overview provides an introduction to the planning steps required in order to deploy Windows Server 2016 or Windows Server 2012 Remote Access in a multisite configuration.

1. [Deploy a Single DirectAccess Server with Advanced Settings](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831436%28v=ws.11%29). This step includes planning for the infrastructure required to deploy a single server. It includes planning for network and server settings, certificate requirements, DNS settings, network location server deployment, DirectAccess management servers, Active Directory settings, and Group Policy objects (GPOs).
2. [Step 2 Plan the multisite infrastructure](step-2-plan-the-multisite-infrastructure). This step includes Active Directory and GPO planning, and DNS configuration.
3. [Step 3 Plan the Multisite Deployment](step-3-plan-the-multisite-deployment). This step includes planning certificate settings, network location server configuration, client entry point settings, IPv6 prefix settings, and optionally global load balancing settings.

Note

Record your planning decisions for Remote Access advanced deployment. This record can be used as a job aid for everyone involved in completing the deployment steps.

After you have completed these planning steps, see [Configuring a multisite deployment](../configure/configure-a-multisite-deployment).