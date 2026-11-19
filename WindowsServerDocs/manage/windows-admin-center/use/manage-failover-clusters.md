---
layout: Conceptual
title: Manage Failover Clusters with Windows Admin Center | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/use/manage-failover-clusters
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn how to manage failover clusters by using Windows Admin Center.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2022-02-28T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 7a131da0-9b7e-c9e1-3536-9c668317585c
document_version_independent_id: 2e572be9-9f47-999b-4c4e-d9801d900b55
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/use/manage-failover-clusters.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/use/manage-failover-clusters
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/use/manage-failover-clusters.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: ced41659-6214-2999-7e80-de8fb6510742
---

# Manage Failover Clusters with Windows Admin Center | Microsoft Learn

Failover Clustering groups multiple servers into a fault-tolerant cluster so that applications and services can remain available if a server fails. Windows Admin Center provides a central interface for managing these clusters, which helps you monitor and maintain cluster resources without managing each node separately.

This article shows you how to add a failover cluster to Windows Admin Center and lists the tools available for managing cluster resources, storage, networks, nodes, roles, virtual machines, and virtual switches. The guidance applies only to failover cluster connections in Windows Admin Center Administration Mode. To manage virtualization clusters in Virtualization Mode, use the virtualization fabric and resource hierarchy.

Tip

New to Windows Admin Center? [Download or learn more about Windows Admin Center](../overview).

![Screenshot of the list of cluster resources in Windows Admin Center.](../media/manage-failover-clusters/fcm-overview.png)

## Add a failover cluster to Windows Admin Center

1. Under **All Connections**, select **+ Add**.
2. Select **Server clusters** as the connection type.
3. Enter the name of the cluster. If you're prompted, enter the credentials to use.
4. Choose whether to add the cluster nodes as individual server connections in Windows Admin Center.
5. Select **Add** to finish.

The cluster is added to your list of connections on the **Overview** page. Select it to connect to the cluster.

Note

You can also manage hyper-converged clusters by adding the cluster as a [hyper-converged cluster connection](manage-hyper-converged) in Windows Admin Center.

## Tools for managing failover clusters

The following areas of Windows Admin Center represent tools that are available for failover cluster connections:

| Area | Description |
| --- | --- |
| **Overview** | View failover cluster details and manage cluster resources. |
| **Disks** | View cluster shared disks and volumes. |
| **Networks** | View networks in the cluster. |
| **Nodes** | View and manage cluster nodes. |
| **Roles** | Manage cluster roles or create an empty role. |
| **Updates** | Manage Cluster-Aware Updating (requires [CredSSP](../understand/faq#does-windows-admin-center-use-credssp-)). |
| **Virtual Machines** | View and manage [virtual machines](manage-virtual-machines). |
| **Virtual Switches** | View and manage virtual switches. |