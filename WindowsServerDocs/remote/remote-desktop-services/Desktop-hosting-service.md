---
layout: Conceptual
title: Desktop hosting service | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/desktop-hosting-service
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn about the desktop hosting service's components in Windows Server.
author: robinharwood
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: concept-article
ms.author: roharwoo
locale: en-us
document_id: 6860dad2-43e4-ec2d-a104-3372a2049c9c
document_version_independent_id: ce129983-70bf-ded4-ce53-2e26850a00b2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/Desktop-hosting-service.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/desktop-hosting-service
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/Desktop-hosting-service.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/6ab7faaf-d791-4a26-96a2-3b11738538e7
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/302e28b0-1f09-4811-9a9b-2a72e0770581
platformId: ba0c64d9-1e74-026f-e2ab-567899476a7a
---

# Desktop hosting service | Microsoft Learn

This article will tell you more about the desktop hosting service's components.

## Tenant environment

As described in [Remote Desktop service roles](rds-roles), each role plays a distinct part in the tenant environment.

The provider's desktop hosting service is implemented as a set of isolated tenant environments. Each tenant's environment consists of a storage container, a set of virtual machines, and a combination of Azure services, all communicating over an isolated virtual network. Each virtual machine contains one or more of the components that make up the tenant's hosted desktop environment. The following subsections describe the components that make up each tenant's hosted desktop environment.

## Active Directory Domain Services

Active Directory Domain Services (AD DS) provides the domain and forest information, such that the tenant's users can sign in to the desktops and applications to carry out their workloads. This also enables you to set up or connect to required file shares and databases that may be required for Windows applications.

The tenant's forest does not require any trust relationship with the provider's management forest. A domain administrator account may be set up in the tenant's domain to allow the provider's technical personnel to perform administrative tasks in the tenant's environment (such as monitoring system status and applying software updates) and to assist with troubleshooting and configuration.

There are multiple ways to deploy AD DS:

1. Enable Microsoft Entra Domain Services in the tenant's virtual networking environment. This will create a managed AD DS instance for the tenant based on the users and groups that exist in Microsoft Entra ID.
2. Set up a stand-alone AD DS server in the tenant's virtual networking environment. This gives you all of the full control of the AD DS instance running on virtual machines.
3. Create a site-to-site VPN connection to an AD DS server located on the tenant's premises. This allows the tenant to connect to their existing AD DS instance and reduce duplication of users, groups, organizational units, and so on.

For more information, see the following articles:

- [Microsoft Entra Domain Services documentation](/en-us/azure/active-directory-domain-services/)
- [Desktop Hosting Reference Architecture Guide](/en-us/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal)
- [Create a site-to-site connection in the Azure portal](/en-us/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal)

## SQL database

A highly-available SQL database is used by the Remote Desktop Connection Broker to store deployment information, such as the mapping of current users' connections to the host servers.

There are multiple ways to deploy an SQL database:

1. Create an Azure SQL Database in the tenant's environment. This provides you with the functionality of a redundant SQL database without you having to manage the servers themselves. This also allows you to pay for what you consume instead of investing in infrastructure.
2. Create an SQL Server AlwaysOn cluster. This allows you to leverage existing SQL Server infrastructure and gives you complete control over the SQL Server instances.

For more information about how to set up a highly-available SQL database infrastructure, see the following articles:

- [What is the Azure SQL Database service?](/en-us/azure/sql-database/sql-database-technical-overview)
- [Creation and configuration of availability groups (SQL Server)](/en-us/sql/database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server?view=sql-server-2017&amp;preserve-view=true).
- [Add the RD Connection Broker server to the deployment and configure high availability](rds-connection-broker-cluster).

## File server

The file server uses the Server Message Block (SMB) 3.0 protocol to provide shared folders. These shared folders are used to create and store user profile disk files (.vhdx) to back up data and let users share data with each other within the tenant's cloud service.

The virtual machine that deploys the file server must have an Azure data disk attached and configured with shared folders. Azure data disks use write-through caching, guaranteeing that writes to the disk will not be erased whenever the virtual machine is restarted.

Small tenants can reduce costs by combining the file server and [RD Licensing role](rds-roles#remote-desktop-licensing) on a single virtual machine in the tenant's environment.

For more information, see the following articles:

- [Storage in Windows Server](../../storage/storage)
- [How to attach a managed data disk to a Windows VM in the Azure portal](/en-us/azure/virtual-machines/windows/attach-managed-disk-portal?toc=/azure/virtual-machines/windows/classic/toc.json)

### User profile disks

User profile disks allow users to save personal settings and files when they are signed in to a session on an RD Session Host server in one collection, then access the same settings and files when signing in to a different [RD Session Host](rds-roles#remote-desktop-session-host) server in the collection. When the user first signs in, the tenant's file server creates a user profile disk that gets mounted to the RD Session Host server that the user is currently connected to. For each subsequent sign-in, the user profile disk is mounted to the appropriate RD Session host server, and it is unmounted with each sign-out. Only the user can access the profile disk's contents.