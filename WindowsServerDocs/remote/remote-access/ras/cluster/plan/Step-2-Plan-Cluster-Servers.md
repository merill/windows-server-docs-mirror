---
layout: Conceptual
title: Step 2 Plan Cluster Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/cluster/plan/step-2-plan-cluster-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to plan to add additional servers to the cluster.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 59d4e877-c7e6-136d-cb2c-1b19efeecbf9
document_version_independent_id: a7de56cf-0646-55b7-df2b-5a4b95081140
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/cluster/plan/Step-2-Plan-Cluster-Servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/cluster/plan/step-2-plan-cluster-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/cluster/plan/Step-2-Plan-Cluster-Servers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 19c300a9-7aaf-0a5b-59ae-bc127da6d6cd
---

# Step 2 Plan Cluster Servers | Microsoft Learn

After deploying a single Remote Access server, plan to add additional servers to the cluster.

| Task | Description |
| --- | --- |
| 2.1 Installing roles and features. | For each server that will be added to the cluster, plan for installation of the Remote Access role and the Windows NLB feature (if needed), plan the topology, IP addressing, routing and forwarding. |
| 2.2 Configure server settings | Configure settings for each server that will be added to the cluster. Note that you can configure a load balanced cluster of servers using virtual machines. In order for routing and connectivity to work correctly, you must configure the virtual machines to use MAC address spoofing. |

## 2.1 Installing roles and features

For each server you want to join to the cluster, plan to install the Remote Access role. In addition plan to install the Network Load Balancing (NLB) feature if you want to load balance traffic to the cluster using Windows NLB. For more information see [Network Load Balancing](../../../../../networking/technologies/network-load-balancing).

## 2.2 Configure server settings

For each server that will be added to the cluster, plan IP address and domain settings. Note the following:

1. Servers in the cluster must all belong to the same domain.
2. Servers in the cluster must be located on the same subnet.
3. Each server in the cluster should have the same number of network adapters in use for the DirectAccess deployment.

When you load balance the cluster using Windows NLB the following Windows NLB settings are applied:

1. Operation mode-Unicast. This can be changed to multicast using NLB Manager. This setting cannot be modified in the Remote Access Management console.
2. Load weight factor-Defined as Equal, where all cluster servers have equal load.
3. Filtering mode-Traffic will be load balanced across multiple hosts.
4. Affinity-Single affinity is defined.
5. Protocols-Both