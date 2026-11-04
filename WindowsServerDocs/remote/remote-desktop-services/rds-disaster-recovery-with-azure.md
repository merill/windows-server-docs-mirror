---
layout: Conceptual
title: Set up disaster recovery for RDS using Azure Disaster Recovery | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-disaster-recovery-with-azure
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to use Azure Disaster Recovery for disaster recovery for an RDS deployment
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
locale: en-us
document_id: 7cd97de4-1318-804c-8dc9-0809945b9e73
document_version_independent_id: 41b66ba1-2639-7371-862f-f5e1d9d44e29
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-disaster-recovery-with-azure.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-disaster-recovery-with-azure
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-disaster-recovery-with-azure.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bba62c59-6b53-4be4-8b9d-6624f9184c22
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/f3a81ffb-ee36-4ec7-b54a-01b6681aff65
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 7d1e1de2-06a8-bed1-dc34-938e2eb599f3
---

# Set up disaster recovery for RDS using Azure Disaster Recovery | Microsoft Learn

You can use Azure Site Recovery to create a disaster recovery solution for your Remote Desktop Services deployment.

[Azure Site Recovery](/en-us/azure/site-recovery/site-recovery-overview) is an Azure-based service that provides disaster recovery capabilities by orchestrating replication, failover, and recovery of virtual machines. Azure Site Recovery supports a number of replication technologies to consistently replicate, protect, and seamlessly failover virtual machines and applications to private/public or hoster's clouds.

Use the following information to create and validate the disaster recovery solution.

## Disaster recovery deployment options

You can deploy RDS on either physical servers or virtual machines running Hyper-V or VMWare. Azure Site Recovery can protect both on-premises and virtual deployments to either a secondary site or to Azure. The following table shows the different supported RDS deployments in site-to-site and site-to-Azure disaster recvoery scenarios.

| Deployment type | Hyper-V site-to-site | Hyper-V site-to-Azure | VMWare site-to-Azure | Physical site-to-Azure |
| --- | --- | --- | --- | --- |
| Pooled virtual desktop (unmanaged) | Yes | No | No | No |
| Pooled virtual desktop (managed, no UPD) | Yes | No | No | No |
| RemoteApps and desktop sessions (no UPD) | Yes | Yes | Yes | Yes |

## Prerequisites

Before you can configure Azure Site Recovery for your deployment, make sure you meet the following requirements:

- Create an [on-premises RDS deployment](rds-deploy-infrastructure).
- Add [Azure Site Recovery Services vault](/en-us/azure/site-recovery/site-recovery-vmm-to-azure#create-a-recovery-services-vault) to your Microsoft Azure subscription.
- If you are going to use Azure as your recovery site, run the [Azure Virtual Machine Readiness Assessment tool](https://azure.microsoft.com/downloads/vm-readiness-assessment/) on your VMs to ensure they are compatible with Azure VMs and Azure Site Recovery Services.

## Implementation checklist

We'll cover the various steps to enable Azure Site Recovery Services for your RDS deployment in more detail, but here are the high-level implementation steps.

| **Step 1 - Configure VMs for disaster recovery** |
| --- |
| Hyper-V - Download the Microsoft Azure Site Recovery Provider. Install it on your VMM server or Hyper-V host. See [Prerequisites for replication to Azure by using Azure Site Recovery](/en-us/azure/site-recovery/site-recovery-prereq) for information. |
| VMWare - Configure protection server, configuration server, and target servers |
| **Step 2 - Prepare your resources** |
| Add an [Azure Storage account](/en-us/azure/storage/storage-create-storage-account). |
| Hyper-V - Download the Microsoft Azure Recovery Services agent and install it on Hyper-V host servers. |
| VMWare - Make sure the mobility service is installed on all VMs. |
| [Enable protection for VMs in VMM cloud, Hyper-V sites, or VMWare sites](rds-enable-dr-with-asr). |
| **Step 3 - Design your recovery plan.** |
| Map your resources - map on-premises networks to Azure VNETs. |
| [Create the recovery plan](rds-disaster-recovery-plan). |
| Test the recovery plan by creating a test failover. Ensure all VMs can access required resources, like Active Directory. Ensure network redirections are configured and working for RDS. For detailed steps on testing your recovery plan, see [Run a test failover](/en-us/azure/site-recovery/site-recovery-test-failover-to-azure) |
| **Step 4 - Run a disaster recovery drill.** |
| Run a disaster recovery drill using planned and unplanned failovers. Ensure that all VMs have access to required resources, such as Active Directory. Ensure that all VMs have access to required resources, such as Active Directory. For detailed steps on failovers and how to run drills, see [Failover in Site Recovery](/en-us/azure/site-recovery/site-recovery-failover). |