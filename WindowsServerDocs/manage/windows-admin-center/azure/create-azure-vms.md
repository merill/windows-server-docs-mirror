---
layout: Conceptual
title: Deploy Azure Virtual Machines using Windows Admin Center | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/azure/create-azure-vms
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Deploying Azure virtual machines with Windows Admin Center. Configuring Azure virtual machines as part of Windows Admin Center-managed scenarios.
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2020-01-28T00:00:00.0000000Z
locale: en-us
document_id: 09578fc1-5b25-a252-cafc-59e753532f2f
document_version_independent_id: 53930633-d16e-fd56-e2ba-a31c2fd33480
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/azure/create-azure-vms.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/azure/create-azure-vms
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/azure/create-azure-vms.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6222df50-3dcf-bcc4-6b2b-3110fef89189
---

# Deploy Azure Virtual Machines using Windows Admin Center | Microsoft Learn

Windows Admin Center version 1910 allows you to deploy Azure virtual machines. This integrates VM deployment into Windows Admin Center-managed workloads like [Storage Migration Service](../../../storage/storage-migration-service/overview) and [Storage Replica](../../../storage/storage-replica/storage-replica-overview). Instead of building new servers and VMs in the Azure Portal by hand prior to deploying your workload - and possibly missing required steps and configuration - Windows Admin Center can deploy the Azure VM, configure its storage, join it to your domain, install roles, and then set up your distributed system. You can also deploy new Azure VMs without a workload from the Windows Admin Center Connections page.

Windows Admin Center also manages a variety of Azure services. [Learn more about the Azure integration options available with Windows Admin Center](./).

If you want to lift and shift virtual machines to Azure instead of creating new ones, consider using Azure Migrate. For more info, see [Azure Migrate overview](/en-us/azure/migrate/migrate-services-overview).

## Scenarios

Windows Admin Center version 1910 Azure VM deployment supports the following scenarios:

- [Storage Migration Service](../../../storage/storage-migration-service/overview)
- [Storage Replica](../../../storage/storage-replica/storage-replica-overview)
- [New standalone server (without roles)](./#extend-on-premises-capacity-with-azure)

## Requirements

Creating a new Azure VM from within Windows Admin Center requires that you have:

- An [Azure subscription](https://azure.microsoft.com).
- A [Windows Admin Center gateway registered with Azure](azure-integration)
- An existing [Azure resource group](/en-us/azure/azure-resource-manager/management/overview) where you have Create permissions.
- An existing [Azure Virtual Network](/en-us/azure/virtual-network/virtual-networks-overview) and subnet.
- An [Azure ExpressRoute](https://azure.microsoft.com/services/expressroute/) circuit or [Azure VPN solution](https://azure.microsoft.com/services/vpn-gateway/) tied to the virtual network and subnet that allows connectivity from Azure VMs to your on-premises clients, domain controllers, the Windows Admin Center computer, and any servers requiring communication with this VM as part of a workload deployment. For instance, to use the Storage Migration Service to migrate storage to an Azure VM, the orchestrator computer and the source computer must both be able to contact the destination Azure VM you are migrating to.

## Usage

Azure VM deployment steps and wizards vary by scenario. Review the workload's documentation for detailed information about the overall scenario.

### Deploying Azure VMs as part of Storage Migration Service

1. From the *Storage Migration Service* tool within Windows Admin Center, perform an inventory of one or more source servers.
2. Once you're in the *Transfer Data* phase, select **Create a new Azure VM** on the *Specify a destination* page then click **Create VM**. This begins a step-by-step creation tool that selects a Windows Server 2012 R2, Windows Server 2016, or Windows Server 2019 Azure VM as a destination for the migration. Storage Migration Service provides recommended VM sizes to match your source, but you can override them by clicking **See all sizes**. Source server data is also used to automatically configure your managed disks and their file systems as well as join your new Azure VM to your Active Directory domain. If the VM is Windows Server 2019 (which we recommend), Windows Admin Center installs the Storage Migration Service proxy feature. Once it has created the Azure VM, Windows Admin Center returns to the normal Storage Migration Service transfer workflow.

Here's a video showing how to use Storage Migration Service to migrate to Azure VMs.

### Deploying Azure VMs as part of Storage Replica

1. From the *Storage Replica* tool within Windows Admin Center, under the *Partnerships* tab, select **New** and then under *Replicate with another server* select **Use a New Azure VM** then select **Next**.
2. Specify your source server information and replication group name, and then select **Next**. This begins a process that automatically selects a Windows Server 2016 or Windows Server 2019 Azure VM as a destination for the migration source. Storage Migration Service recommends VM sizes to match your source, but you can override this by selecting **See all sizes**. Inventory data is used to automatically configure your managed disks and their file systems, as well as join your new Azure VM to your Active Directory domain.
3. After Windows Admin Center creates the Azure VM, provide a replication group name and then select **Create**. Windows Admin Center then begins the normal Storage Replica initial synchronization process to start protecting your data.

Here's a video showing how to use Storage Replica to replicate to Azure VMs.

### Deploying a new standalone Azure VM

1. From the *All Connections* page within Windows Admin Center, select **Add**.
2. In the *Azure VM* section, select **Create new**. This begins a step-by-step creation tool that will let you select a Windows Server 2012 R2, Windows Server 2016, or Windows Server 2019 Azure VM, pick a size, add managed disks, and optionally join your Active Directory domain.

Here's a video showing how to use Windows Admin Center to create Azure VMs.