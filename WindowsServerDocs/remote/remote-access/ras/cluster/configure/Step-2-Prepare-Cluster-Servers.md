---
layout: Conceptual
title: Step 2 Prepare Cluster Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/cluster/configure/step-2-prepare-cluster-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to prepare additional servers to add to the cluster.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: ce3ccaf1-c015-aab9-e834-f46e5747ede9
document_version_independent_id: 4f61f3ac-4279-be17-2444-49e6cf94388c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/cluster/configure/Step-2-Prepare-Cluster-Servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/cluster/configure/step-2-prepare-cluster-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/cluster/configure/Step-2-Prepare-Cluster-Servers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 0359c51d-d3b5-eac6-9788-60a1be6bbb8f
---

# Step 2 Prepare Cluster Servers | Microsoft Learn

Before you can configure a cluster deployment, you prepare additional servers to add to the cluster.

| Task | Description |
| --- | --- |
| 2.1 Configure the Remote Access infrastructure | On each server you want to add to the cluster, configure the server topology, IP addressing, routing, and forwarding. If you configure a load balanced cluster of virtual machines, you must configure the virtual machines to use MAC address spoofing.<br>In addition, join each server to the same domain, and connect all the servers to the same subnet. |
| 2.2 Install the Remote Access role | On each additional server you want to add to the cluster, install the Remote Access role |
| 2.3 Install NLB | On the deployed Remote Access server and on each additional server you want to add to the cluster, install the NLB feature. Note that this step is not required when using an External Load Balancer. |

## 2.1 Configure the Remote Access infrastructure

To configure a Remote Access cluster, you must configure the server topology, IP addressing, routing, and forwarding on every server that will form part of the cluster.

### To configure the Remote Access infrastructure

1. Configure each of the servers that will be in the cluster with the same topology as the first Remote Access server.
2. Configure each of the servers that will be in the cluster with appropriate IP addressing, routing, and forwarding based on the configuration of the first Remote Access server. Note that all the servers in the cluster must be connected to the same subnet.
3. Join each of the servers that will be in the cluster to the same domain as the first Remote Access server.

## 2.2 Install the Remote Access role

To configure a Remote Access cluster, you must install the Remote Access role on every server that will form a part of the cluster.

### To install the Remote Access role on Always On VPN servers

1. On the DirectAccess server, in the Server Manager console, in the **Dashboard**, click **Add roles and features**.
2. Click **Next** three times to get to the server role selection screen.
3. On the **Select Server Roles** dialog, select **Remote Access**, and then click **Next**.
4. Click **Next** three times.
5. On the **Select role services** dialog, select **DirectAccess and VPN (RAS)** and then click **Add Features**.
6. Select **Routing**, select **Web Application Proxy**, click **Add Features**, and then click **Next**.
7. Click **Next**, and then click **Install**.
8. On the **Installation progress** dialog, verify that the installation was successful, and then click **Close**.
9. Repeat this procedure on all servers that you want to be cluster members.

## 2.3 Install NLB

To configure a Remote Access cluster, you must install the Network Load Balancing feature on every server that will form a part of the cluster.

Note

This step is not required if an external load balancer is used.

#### To install the NLB role

1. On the DirectAccess server, in the Server Manager console, in the **Dashboard**, click **Add roles and features**.
2. Click **Next** four times to get to the server feature selection screen.
3. On the **Select features** dialog, select **Network Load Balancing**, click **Add Features**, click **Next**, and then click **Install**.
4. On the **Installation progress** dialog, verify that the installation was successful, and then click **Close**.
5. Repeat this procedure on all servers that you want to be cluster members.

## See also

- [Step 3: Configure a load-balanced cluster](step-3-configure-a-load-balanced-cluster)