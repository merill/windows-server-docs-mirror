---
layout: Conceptual
title: Plan a Remote Access Cluster Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/cluster/plan/plan-a-remote-access-cluster-deployment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn about the planning steps required in order to deploy a cluster of Windows Server 2016 or Windows Server 2012 Remote Access servers.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: c7588744-e1a1-7038-d9e1-da15da049176
document_version_independent_id: 41df6ff7-603e-3b37-e05a-fc79e9565a03
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/cluster/plan/Plan-a-Remote-Access-Cluster-Deployment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/cluster/plan/plan-a-remote-access-cluster-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/cluster/plan/Plan-a-Remote-Access-Cluster-Deployment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 21dc7abe-2c1f-40ab-c383-68008916c4de
---

# Plan a Remote Access Cluster Deployment | Microsoft Learn

Windows Server 2016 and Windows Server 2012 combine DirectAccess and Remote Access Service (RAS) VPN into a single Remote Access role. This overview provides an introduction to the planning steps required in order to deploy a cluster of Windows Server 2016 or Windows Server 2012 Remote Access servers.

- [Plan an Advanced DirectAccess Deployment](../../../directaccess/single-server-advanced/plan-an-advanced-directaccess-deployment). This step includes planning for the infrastructure required to deploy a single server. It includes planning for network and server settings, certificate requirements, DNS settings, network location server deployment, DirectAccess management servers, Active Directory settings, and Group Policy Objects (GPOs).
- [Step 2 Plan Cluster Servers](step-2-plan-cluster-servers) .
- [Step 3 Plan a Load-Balanced Cluster Deployment](step-3-plan-a-load-balanced-cluster-deployment).
- Step 4: Record your planning decisions for Remote Access advanced deployment. This record can be used as a job aid for everyone involved in completing the deployment steps.

After you have completed these planning steps, see [Configure a Remote Access cluster](../configure/configure-a-remote-access-cluster).

For instructions on configuring a cluster deployment as a proof of concept in a lab environment, see [Test Lab Guide - Demonstrate DirectAccess in a Cluster with Windows NLB](../../../directaccess/tlg-cluster-nlb/test-lab-guide-demonstrate-directaccess-in-a-cluster-with-windows-nlb).