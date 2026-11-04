---
layout: Conceptual
title: Simplified SMB Multichannel and Multi-NIC Cluster Networks | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/failover-clustering/smb-multichannel
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: failover-clustering
ms.update-cycle: 1095-days
description: Learn more about Simplified SMB Multichannel and Multi-NIC Cluster Networks.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2025-01-24T00:00:00.0000000Z
locale: en-us
document_id: 0afc2ef6-663a-92fb-a911-43337091e0c6
document_version_independent_id: 62c36af9-5222-53b3-981d-97a3ccfdbb28
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/failover-clustering/smb-multichannel.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: failover-clustering/smb-multichannel
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/failover-clustering/smb-multichannel.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c54fa0b1-0886-0549-e804-0983e13dcaf4
---

# Simplified SMB Multichannel and Multi-NIC Cluster Networks | Microsoft Learn

Simplified SMB Multichannel and Multi-Network Interface Card (NIC) Cluster Networks is a feature that enables the use of multiple NICs on the same cluster network subnet, and automatically enables SMB Multichannel.

Simplified SMB Multichannel and Multi-NIC Cluster Networks provide the following benefits:

- Failover Clustering automatically recognizes all NICs on nodes that are using the same switch / same subnet - no extra configuration needed.
- SMB Multichannel is enabled automatically.
- Networks that only have IPv6 Link Local (fe80) IP Addresses resources are recognized on cluster-only (private) networks.
- A single IP Address resource is configured on each Cluster Access Point (CAP) Network Name (NN) by default.
- Cluster validation no longer issues warning messages when multiple NICs are found on the same subnet.

## Prerequisites

- Multiple NICs per server, using the same switch / subnet.

## How to take advantage of multi-NIC clusters networks and simplified SMB multichannel

This section describes how to take advantage of the new multi-NIC clusters networks and simplified SMB multichannel features.

### Use at least two networks for Failover Clustering

Although it's rare, network switches can fail - it's still best practice to use at least two networks for Failover Clustering. All networks that are found are used for cluster heartbeats. Avoid using a single network for your Failover Cluster in order to avoid a single point of failure. Ideally, there are multiple physical communication paths between the nodes in the cluster, and no single point of failure.

![Illustration of two networks for Failover Clustering.](media/simplified-smb-multichannel-and-multi-nic-cluster-networks/clustering_mulitnic_fig1.png)

**Figure 1: Use at least two networks for Failover Clustering**

### Use Multiple NICs across clusters

Maximum benefit of the simplified SMB multichannel is achieved when multiple NICs are used across clusters - in both storage and storage workload clusters. This allows the workload clusters (Hyper-V, SQL Server Failover Cluster Instance, Storage Replica, etc.) to use SMB multichannel and results in more efficient use of the network. In a converged (also known as disaggregated) cluster configuration where a Scale-out File Server cluster is used for storing workload data for a Hyper-V or SQL Server Failover Cluster Instance cluster, this network is often called "the North-South subnet" / network. Many customers maximize throughput of this network by investing in RDMA capable NIC cards and switches.

![Illustration of a North-South SMB Subnet.](media/simplified-smb-multichannel-and-multi-nic-cluster-networks/clustering_mulitnic_fig2.png)

**Figure 2: To achieve maximum network throughput, use multiple NICs on both the Scale-out File Server cluster and the Hyper-V or SQL Server Failover Cluster Instance cluster - which share the North-South subnet**

![Screenshot of two clusters using multiple NICs in the same subnet to leverage SMB multichannel.](media/simplified-smb-multichannel-and-multi-nic-cluster-networks/clustering_mulitnic_fig3.png)

**Figure 3: Two clusters (Scale-out File Server for storage, SQL Server Failover Clustering Instance (FCI) for workload) both use multiple NICs in the same subnet to leverage SMB Multichannel and achieve better network throughput.**

## Automatic recognition of IPv6 Link Local private networks

When using more than one private (cluster only) network, check the IPv6 routing configuration to ensure that routing isn't configured to cross subnets, since this reduces network performance.

When using more than one private (cluster only) network, check the IPv6 routing configuration to ensure that routing isn't configured to cross subnets, since this reduces network performance.

![Screenshot of automatic network configuration in the Failover Cluster Manager UI.](media/simplified-smb-multichannel-and-multi-nic-cluster-networks/clustering_mulitnic_fig4.png)

**Figure 4: Automatic IPv6 Link Local (fe80) Address resource configuration**

## Throughput and Fault Tolerance

Windows Server 2016 and later automatically detect NIC capabilities and attempt to use each NIC in the fastest possible configuration. NICs that are teamed, NICs using RSS, and NICs with RDMA capability can all be used. The table below summarizes the trade-offs when using these technologies. Maximum throughput is achieved when using multiple RDMA capable NICs. For more information, see [The basics of SMB multichannel](/en-us/archive/blogs/josebda/the-basics-of-smb-multichannel-a-feature-of-windows-server-2012-and-smb-3-0).

![An illustration of throughput and fault tolerance for various NIC configurations.](media/simplified-smb-multichannel-and-multi-nic-cluster-networks/clustering_mulitnic_fig5.png)

**Figure 5: Throughput and fault tolerance for various NIC configurations**

## Frequently asked questions

**Are all NICs in a multi-NIC network used for cluster heart beating?** Either configuration works - all cluster network roles work on a multi-NIC network.

**Can a multi-NIC network be used for cluster communication only? Or can it only be used for client and cluster communication?** Yes, by default all cluster and CSV traffic use available multi-NIC networks. Administrators can use the Failover Clustering PowerShell cmdlets or Failover Cluster Manager UI to change the network role.

**Is SMB Multichannel also used for CSV and cluster traffic?** Yes, by default all cluster and CSV traffic use available multi-NIC networks. Administrators can use the Failover Clustering PowerShell cmdlets or Failover Cluster Manager UI to change the network role.

**How can I see the SMB Multichannel settings?** Use the **Get-SMBServerConfiguration** cmdlet, look for the value of the EnableMultiChannel property.

**Is the cluster common property PlumbAllCrossSubnetRoutes respected on a multi-NIC network?** Yes.