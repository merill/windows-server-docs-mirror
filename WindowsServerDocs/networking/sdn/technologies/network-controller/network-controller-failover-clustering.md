---
layout: Conceptual
title: Network Controller with Failover Clustering on Windows Server and Azure Local | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/technologies/network-controller/network-controller-failover-clustering
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: Learn about Network Controller high availability using Failover Clustering for Software Defined Networking (SDN) in Windows Server and Azure Local.
author: robinharwood
ms.author: roharwoo
ms.topic: concept-article
ms.date: 2024-12-06T00:00:00.0000000Z
zone_pivot_groups: windows-os
locale: en-us
document_id: dd0d7c19-83a8-2619-627f-049481dfc9ce
document_version_independent_id: dd0d7c19-83a8-2619-627f-049481dfc9ce
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/technologies/network-controller/network-controller-failover-clustering.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/technologies/network-controller/network-controller-failover-clustering
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/technologies/network-controller/network-controller-failover-clustering.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/289b8734-3abd-4162-bc19-e661c3f4c940
- https://authoring-docs-microsoft.poolparty.biz/devrel/e23899b2-c37a-45de-abc2-b8ae68bc8d1b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a94795e-9024-410d-b38e-b67941440893
- https://authoring-docs-microsoft.poolparty.biz/devrel/240a460b-6952-41c5-8dde-f348a35b5727
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b4e5450a-88d5-8c5a-40c6-363e68d94a9b
---

# Network Controller with Failover Clustering on Windows Server and Azure Local | Microsoft Learn

::: zone pivot="windows-server"

Beginning with Windows Server 2025 Software Defined Networking infrastructure uses a smaller footprint for the Network Controller (NC), one of the core infrastructural components. NC can now be deployed directly on the host as a Failover Clustering service. Service Fabric based infrastructure continues to be supported. This article provides an overview of Network Controller high availability using Failover Clustering, how it works with Software Load Balancer and Gateways, and how it differs from Network Controller on Service Fabric.

::: zone-end

::: zone pivot="azure-local"

Beginning with Azure Local 2311.2, Software Defined Networking infrastructure uses a smaller footprint for the Network Controller (NC), one of the core infrastructural components. NC can now be deployed directly on the host as a Failover Clustering service. Service Fabric based infrastructure continues to be supported. This article provides an overview of Network Controller high availability using Failover Clustering, how it works with Software Load Balancer and Gateways, and how it differs from Network Controller on Service Fabric.

::: zone-end

## Network Controller as a role

Network Controller is a key component of the SDN ecosystem. It allows you to deploy and manage your tenant network configurations, including virtual networking, logical networking, and network security. In previous versions of Windows Server and Azure Local, Network Controller had to be hosted inside a VM. VM-based resource deployment is a long and resource-intensive. VMs took up more CPU and Memory, resources that could be spent on your core application workloads. Beginning with Windows Server 2025 and Azure Local 2311.2, the NC service will be natively integrated with the host machine using Failover Clustering, freeing up resources for your other workloads. The following illustration provides an overview of the key differences between NC on Service Fabric and NC on Failover Clustering.

[![A diagram comparing the differences between Network Controller with Failover Clustering and Network Controller with Service Fabric.](../../../media/network-controller-failover-cluster/failover-cluster-service-fabric-comparison.png)](../../../media/network-controller-failover-cluster/failover-cluster-service-fabric-comparison.png#lightbox)

## Architecture

With Network Controller on Failover Clustering, all the Network Controller microservices are now contained in a failover cluster resource group. SDN microservices use a single database and single partition, rather than three databases duplicated across 3 VMs when using Service Fabric. With each SDN microservice as a Failover Clustering resource group, there’s a significant reduction in CPU utilization and storage.

Network Controller and all its services are set as a Failover Cluster group set across the servers in your Software Defined Networking cluster. For example, your network topology includes four servers clustered together with a single Top-of-Rack (ToR) Switch, and the Network Controller component as a *Failover Clustering Generic Resource* is spread across all servers. Instead of the three VMs in previous versions, each Network Controller microservice is highly available as a Failover Cluster Resource Group. The following diagram shows a 4-node deployment with Network Controller on Failover Clustering.

[![A diagram showing a 4-node deployment with Network Controller on Failover Clustering](../../../media/network-controller-failover-cluster/concept.png)](../../../media/network-controller-failover-cluster/concept.png#lightbox)

The resource group has the same provisioning requirements as NC VMs. The API Microservice requires a floating IP address in your management network and DNS registration is still supported.

## High Availability

With Network Controller on Failover Clustering, resource ownership is associated with a specific node within the Failover Cluster. When a server goes down, resource groups are transferred to another node within the cluster. Replication of data is done through the underlying infrastructure of Failover Clustering which is Storage Replica. To learn more about Failover Clustering and Storage Replica, see the following resources:

::: zone pivot="windows-server"

- [Failover Clustering in Windows Server and Azure Local](../../../../failover-clustering/failover-clustering-overview)
- [Storage Replica Overview](../../../../storage/storage-replica/storage-replica-overview)

::: zone-end

::: zone pivot="azure-local"

- [Failover Clustering in Windows Server and Azure Local](../../../../failover-clustering/failover-clustering-overview?context=/azure-local/context/context)
- [Storage Replica Overview](../../../../storage/storage-replica/storage-replica-overview?context=/azure-local/context/context)

::: zone-end

## Software Load Balancing and Gateways

This transition from Service Fabric to Failover Clustering only affects our Network Controlling services. Other network function virtualization roles, such as the Software Load Balancer and Gateway are still hosted on Virtual Machines. Network Controller on Failover Clustering doesn't affect the behavior or operation of other network function virtualization roles. For more details on Software Load Balancing and Gateways, visit the following links:

- [What is Software Load Balancer (SLB) for SDN?](/en-us/azure/azure-local/concepts/software-load-balancer)
- [What is Remote Access Service (RAS) Gateway for Software Defined Networking?](/en-us/azure/azure-local/concepts/gateway-overview)