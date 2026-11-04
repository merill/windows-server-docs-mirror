---
layout: Conceptual
title: Storage Migration Service overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/storage-migration-service/overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Storage Migration Service makes it easier to migrate storage to Windows Server or to Azure. It provides a graphical tool that inventories data on Windows, Linux, and NetApp CIFS servers and then transfers the data to newer servers or to Azure virtual machines. Storage Migration Service also provides the option to transfer the identity of a server to the destination server so that apps and users can access their data without changing links or paths.
author: robinharwood
ms.author: roharwoo
ms.date: 2024-06-25T00:00:00.0000000Z
ms.topic: overview
locale: en-us
document_id: 293dff88-4f13-d13a-bf54-4166598e0b81
document_version_independent_id: 58d2fc54-4f15-a67b-94f3-197e2dac7bc7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/storage-migration-service/overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/storage-migration-service/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/storage-migration-service/overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/5bfc2259-d89d-4d6b-97d7-584a51208ec1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e3dafb9-38f2-4708-bb18-eecf2c0a9843
platformId: 17a4983a-11eb-0694-e1fc-67bef8b3f630
---

# Storage Migration Service overview | Microsoft Learn

Storage Migration Service makes it easier to migrate storage to Windows Server or to Azure. It provides a graphical tool that inventories data on Windows, Linux, and NetApp CIFS servers and then transfers the data to newer servers or to Azure virtual machines. Storage Migration Service also provides the option to transfer the identity of a server to the destination server so that apps and users can access their data without changing links or paths.

This article discusses the following Storage Migration Service aspects:

- Why you'd want to use Storage Migration Service.
- How the migration process works.
- What the requirements are for source and destination servers.
- [What's new in Storage Migration Service](../../get-started/whats-new-in-windows-server-2019#storage-migration-service).

## Why use Storage Migration Service

Use Storage Migration Service because you've got a server or multiple servers that you want to migrate to newer hardware or virtual machines. Storage Migration Service is designed to help by doing the following tasks:

- Inventory multiple servers and their data
- Rapidly transfer files, file shares, and security configuration from the source servers
- Optionally take over the identity of the source servers (also known as cutting over) so that users and apps don't have to change anything to access existing data
- Manage one or multiple migrations from the Windows Admin Center user interface

![Diagram showing Storage Migration Service migrating files and configuration from source servers to destination servers, Azure VMs, or Azure File Sync.](media/overview/storage-migration-service-diagram.png)

## How the migration process works

Migration is a three-step process:

1. **Inventory servers** to gather info about their files and configuration, shown in the following figure.

    ![Screenshot showing that a server is ready to be scanned.](media/migrate/inventory.png)
2. **Transfer (copy) data** from the source servers to the destination servers.
3. **Cut over to the new servers** (optional).The destination servers assume the source servers' former identities so that apps and users don't have to change anything. The source servers enter a maintenance state where they still contain the same files they always have (we never remove files from the source servers) but are unavailable to users and apps. You can then decommission the servers at your convenience.

The following video shows how to use Storage Migration Service to take a server, such as a Windows Server 2008 R2 server that's out of support, and move the storage to a newer server.

## Requirements

To use Storage Migration Service, you need the following items:

- A **source server** or **failover cluster** to migrate files and data from.
- A **destination server** running Windows Server 2019 or later (clustered or standalone) to migrate to. While Windows Server 2016 is also supported, it may be more difficult to migrate to and its support will end in January 2027.
- An **orchestrator server** running Windows Server 2019 or later to manage the migration. If you're migrating only one server, you can use the destination as the orchestrator. If you're migrating several servers, use a separate orchestrator server.
- A **PC or server running the latest [Windows Admin Center](../../manage/windows-admin-center/overview)** to run the Storage Migration Service user interface, along with the latest Storage Migration Service tool (extension) available from the feed.

We strongly recommend that the orchestrator and destination computers have at least two cores or two vCPUs and at least 2 GB of memory. Inventory and transfer operations are faster with more processors and memory.

### Security requirements, the Storage Migration Service proxy service, and firewall ports

- A migration account that is an administrator on the source computers and the orchestrator computer. This account can be a domain or local account except in the case of a computer that isn't joined to the domain, in which case it must be a local user.
- A migration account that is an administrator on the destination computers and the orchestrator computer. This account can be a domain or local account except in the case of a computer that isn't joined to the domain, in which case it must be a local user.
- The orchestrator computer must have the File and Printer Sharing (SMB-In) firewall rule enabled *inbound*.
- The source and destination computers must have the following firewall rules enabled *inbound* (although you might already have them enabled):

    - File and Printer Sharing (SMB-In)
    - Netlogon Service (NP-In)
    - Windows Management Instrumentation (DCOM-In)
    - Windows Management Instrumentation (WMI-In)

    Tip

    Installing the Storage Migration Service Proxy service on a destination computer automatically opens the necessary firewall ports on that computer. To do so, connect to the destination server in Windows Admin Center and then go to **Server Manager** (in Windows Admin Center) &gt; **Roles and features**, select **Storage Migration Service Proxy**, and then choose **Install**.
- If the computers belong to an Active Directory Domain Services domain, they should all belong to the same forest. The destination server must also be in the same domain as the source server if you want to transfer the source's domain name to the destination when cutting over. While cutover works across domains, the fully qualified domain name of the destination is different from the source and using two different domains will likely cause DNS issues.

### Requirements for source servers

The source server must run one of the following operating systems:

- Windows Server, Semi-Annual Channel
- Windows Server 2025
- Windows Server 2022
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2
- Windows Server 2008
- Windows Server 2003 R2
- Windows Server 2003
- Windows Small Business Server 2003 R2
- Windows Small Business Server 2008
- Windows Small Business Server 2011
- Windows Server 2012 Essentials
- Windows Server 2012 R2 Essentials
- Windows Server 2016 Essentials
- Windows Server 2019 Essentials
- Windows Storage Server 2008
- Windows Storage Server 2008 R2
- Windows Storage Server 2012
- Windows Storage Server 2012 R2
- Windows Storage Server 2016

Note

Windows Small Business Server and Windows Server Essentials are domain controllers. Storage Migration Service can't cut over from domain controllers, but it can inventory and transfer files from them.

You can migrate the following other source types if the orchestrator is running Windows Server 2019 with [KB5001384](https://support.microsoft.com/topic/april-20-2021-security-update-kb5001384-e471f445-59be-42cb-8c57-5db644cbc698) installed or Windows Server 2022:

- Failover clusters running Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2. Windows Server 2008 R2 only supports inventory and transfer, not cutover.
- Linux servers that use Samba. We've tested the following distributions:
    - CentOS 7
    - Debian GNU/Linux 8
    - RedHat Enterprise Linux 7.6
    - SUSE Linux Enterprise Server (SLES) 11 SP4
    - Ubuntu 16.04 LTS and 12.04.5 LTS
    - Samba 4.8, 4.7, 4.3, 4.2, and 3.6
- NetApp FAS arrays hosting NetApp CIFS server, running NetApp ONTAP 9.

### Requirements for destination servers

The destination server must run one of the following operating systems:

- Windows Server, Semi-Annual Channel
- Windows Server 2025
- Windows Server 2022
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2

The destination servers can be standalone servers or a Windows failover cluster. Be aware that the clusters themselves are not migrated, solely the file server cluster resources. They can't run Azure Local or use a non-Microsoft clustering add-on. While the Storage Migration Service doesn't support Azure Files as a destination, it fully supports servers running the Azure File Sync agent with cloud tiering.

Tip

Destination servers running Windows Server 2019 or later have double the transfer performance of earlier versions of Windows Server. This performance boost is due to the inclusion of a built-in Storage Migration Service proxy service.

## Azure VM migration

Windows Admin Center integrates Azure IaaS deployment into Storage Migration Service. It lets you avoid building new servers and VMs in the Azure portal by hand prior to deploying your workload. It also lets you avoid possibly missing required steps and configuration. Windows Admin Center can deploy the Azure IaaS VM, configure its storage, join it to your domain, install roles, and then set up your distributed system.

The following video shows how to use Storage Migration Service to migrate to Azure VMs.

If you want to lift and shift virtual machines to Azure without migrating to a later operating system, consider using Azure Migrate. For more information, see [About Azure Migrate](/en-us/azure/migrate/migrate-services-overview).

## Related links

- [Use Storage Migration Service to migrate a server](migrate-data)
- [Storage Migration Service frequently asked questions (FAQ)](faq)
- [Storage Migration Service known issues](known-issues)