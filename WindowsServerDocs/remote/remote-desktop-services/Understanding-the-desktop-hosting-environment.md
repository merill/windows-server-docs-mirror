---
layout: Conceptual
title: Understanding the desktop hosting environment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/understanding-the-desktop-hosting-environment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Overview of an RDS deployment using Azure IaaS.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: concept-article
author: robinharwood
locale: en-us
document_id: 9a6abb7b-7c53-15e1-bd27-8d17c7fde520
document_version_independent_id: 4e4bc9bc-eec2-2700-4223-488390e77b93
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/Understanding-the-desktop-hosting-environment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/understanding-the-desktop-hosting-environment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/Understanding-the-desktop-hosting-environment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 4026c42b-18ef-8ff6-cba8-4689933d3f11
---

# Understanding the desktop hosting environment | Microsoft Learn

The following information describes the components of the desktop hosting service.

## Tenant environment

The provider's desktop hosting service is implemented as a set of isolated tenant environments. Each tenant's environment consists of a storage container, a set of virtual machines, and a combination of Azure services, all communicating over an isolated virtual network. Each virtual machine contains one or more of the components that make up the tenant's hosted desktop environment. The following subsections describe the components that make up each tenant's hosted desktop environment.

## Remote Desktop Services

In a desktop hosting environment, the following Remote Desktop Services roles are installed amongst various virtual machines:

- Remote Desktop Connection Broker
- Remote Desktop Gateway
- Remote Desktop Licensing
- Remote Desktop Session Host
- Remote Desktop Web Access

For a full description of each of these roles and how they interact with each other, please review the [Understanding RDS roles](desktop-hosting-service) document.

## (Azure) Active Directory Domain Services

There are multiple ways to connect to and manage Active Directory Domain Services (AD DS) for a desktop hosting environment in Azure:

1. Create a virtual machine in the tenant's environment running the AD DS role
2. Create a site-to-site VPN connection with the tenant's on-premises environment to use an existing AD DS
3. Use the Microsoft Entra Domain Services PaaS role, which creates a domain on the tenant's virtual network based on the tenant's Microsoft Entra ID

With Remote Desktop Services, the tenant must have an Active Directory to manage access into the environment, user profile storage, and monitoring within the deployment. When using the standard (non-Azure) AD DS, the tenant's forest does not require any trust relationship with the provider's management forest. A domain administrator account may be set up in the tenant's domain to allow the provider's technical personnel to perform administrative tasks in the tenant's environment (such as monitoring system status and applying software updates) and to assist with troubleshooting and configuration.

Additional information: [Microsoft Entra Domain Services Documentation](/en-us/azure/active-directory-domain-services/)[Install a new Active Directory forest on an Azure virtual network](../../identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100)[Create a resource manager VNet with a Site-to-Site VPN connection using the Azure Portal](/en-us/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal)

## Azure SQL Database

Azure SQL Database allows for hosters to extend their Remote Desktop Services deployment without needing to deploy and maintain a full SQL Server Always-On cluster. The Azure SQL Database is used by the Remote Desktop Connection Broker to store deployment information, such as the mapping of current users' connections to end-host servers. Like other Azure services, Azure SQL DB follows a consumption model, ideal for any size deployment.

Additional information: [What is SQL Database?](/en-us/azure/azure-sql/database/sql-database-paas-overview)

## Microsoft Entra application proxy

Microsoft Entra application proxy is a service provided in paid-SKUs of Microsoft Entra ID that allow users to connect to internal applications through Azure's own reverse-proxy service. This allows the RD Web and RD Gateway endpoints to be hidden inside of the virtual network, eliminating the need to be exposed to the internet via a public IP address. This further allows hosters to condense the number of virtual machines in the tenant's environment while still maintaining a full deployment.

Additional information: [Enabling Microsoft Entra application proxy](/en-us/azure/active-directory/app-proxy/application-proxy-config-how-to)

## File server

The file server provides shared folders by using the Server Message Block (SMB) 3.0 protocol. The shared folders are used to create and store user profile disk files (.vhdx), to backup data, and to allow users a place to share data with other users in the tenant's virtual network.

The VM used to deploy the file server must have an Azure data disk attached and configured with shared folders. Azure data disks use write-through caching which guarantees that writes to the disk persist across restarts of the VM.

For small tenants, the cost can be reduced by combining the file server with the virtual machine running the RD Connection Broker and RD Licensing roles on a single virtual machine in the tenant's environment.

Additional information [File and Storage Services Overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831487%28v=ws.11%29)[How to Attach a Data Disk to a Virtual Machine](/en-us/shows/azure-documentation-shorts/attaching-data-disk-to-windows-vm)

### User Profile Disks

User profile disks allow users to save personal settings and files when they are signed in to a session on an RD Session Host server in a collection, and then have access to the same settings and files when signing in to a different RD Session Host server in the collection. When the user first signs in, a user profile disk is created on the tenant's file server, and that disk is mounted to the RD Session Host server to which the user is connected. For each subsequent sign-in, the user profile disk is mounted to the appropriate RD Session host server, and with each sign-out, it is un-mounted. The contents of the profile disk can only be accessed by that user.