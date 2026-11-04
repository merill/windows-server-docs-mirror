---
layout: Conceptual
title: Azure services and considerations for desktop hosting | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/azure-services-and-considerations-for-desktop-hosting
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn about considerations unique to Azure with a Remote Desktop hosting solution.
author: robinharwood
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: reference-architecture
ms.author: roharwoo
locale: en-us
document_id: 7f84c096-8f71-39a7-71c5-3d28822aa98e
document_version_independent_id: 57c94b1b-2cff-469b-e68f-29742e60f1c4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/Azure-services-and-considerations-for-desktop-hosting.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/azure-services-and-considerations-for-desktop-hosting
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/Azure-services-and-considerations-for-desktop-hosting.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/f98c9a19-e481-4f15-8047-76b641e6ed57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/f5685781-a4fd-40f1-8126-59abde4643bf
platformId: dfda50f8-c473-c8a5-3846-4a1bf093671c
---

# Azure services and considerations for desktop hosting | Microsoft Learn

The following sections describe Azure Infrastructure Services.

## Azure portal

After the provider creates an Azure subscription, the Azure portal can be used to manually create each tenant's environment. This process can also be automated using PowerShell scripts.

For more information, visit the [Microsoft Azure](https://www.azure.microsoft.com) website.

## Azure Load Balancer

The tenant's components run on virtual machines that communicate with each other on an isolated network. During the deployment process, you can externally access these virtual machines through the Azure Load Balancer using Remote Desktop Protocol endpoints or a Remote PowerShell endpoint. Once a deployment is complete, these endpoints will typically be deleted to reduce the attack surface area. The only endpoints will be the HTTPS and UDP endpoints created for the virtual machine running the RD Web and RD Gateway components. This allows clients on the internet to connect to sessions running in the tenant's desktop hosting service. If a user opens an application that connects to the internet, such as a web browser, the connections will be passed through the Azure Load Balancer.

For more information, see [What is Azure Load Balancer?](/en-us/azure/load-balancer/load-balancer-overview)

## Security considerations

This Azure Desktop Hosting Reference Architecture Guide is designed to provide a highly secure and isolated environment for each tenant. System security also depends on safeguards taken by the provider during deployment and operation of the hosted service. The following list describes some considerations the provider should take to keep their desktop hosting solution based on this reference architecture secure.

- All administrative passwords must be strong, ideally randomly generated, changed frequently, and saved in a secure central location only accessible to a select few provider administrators.
- When replicating the tenant environment for new tenants, avoid using the same or weak administrative passwords.
- The RD Web Access site URL, name, and certificates must be unique and recognizable to each tenant to prevent spoofing attacks.
- During the normal operation of the desktop hosting service, all public IP addresses should be deleted for all virtual machines except the RD Web and RD Gateway virtual machine that lets users securely connect to the tenant's desktop hosting cloud service. Public IP addresses may be temporarily added when necessary for management tasks, but they should always be deleted afterwards.

For more information, see the following articles:

- [Security and protection](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831778%28v=ws.11%29)
- [Security best practices for IIS 8](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj635855%28v=ws.11%29)

## Design considerations

It's important to consider the constraints of Microsoft Azure Infrastructure Services when designing a multitenant desktop hosting service. The following list describes considerations the provider must take to achieve a functional and cost-effective desktop hosting solution based on this reference architecture.

- An Azure subscription has a maximum number of virtual networks, VM cores, and Cloud Services that can be used. If a provider needs more resources than this, they may need to create multiple subscriptions.
- An Azure Cloud Service has a maximum number of virtual machines that can be used. The provider may need to create multiple Cloud Services for larger tenants that exceed the maximum.
- Azure deployment costs are based partially on the number and size of virtual machines. The provider should optimize the number and size of the virtual machines for each tenant to provide a functional and highly secure Desktop Hosting environment at the lowest cost.
- The physical computer resources in the Azure data center are virtualized by using Hyper-V. Hyper-V hosts are not configured in host clusters, so the availability of the virtual machines is dependent on the availability of the individual servers used in the Azure infrastructure. To provide higher availability, multiple instances of each role service virtual machine can be created in an availability set, then guest clustering can be implemented within the virtual machines.
- In a typical storage configuration, a service provider will have a single storage account with multiple containers (for example, one for each tenant), and multiple disks within each container. However, there is a limit to the total storage and performance that can be achieved for a single storage account. For service providers that support large numbers of tenants or tenants with high storage capacity or performance requirements, the service provider may need to create multiple storage accounts.

For more information, see the following articles:

- [Sizes for Cloud Services](/en-us/azure/cloud-services/cloud-services-sizes-specs)
- [Microsoft Azure virtual machine pricing details](https://azure.microsoft.com/pricing/details/virtual-machines/)
- [Hyper-V overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831531%28v=ws.11%29)
- [Azure Storage scalability and performance targets](/en-us/azure/storage/common/storage-scalability-targets)

## Microsoft Entra application proxy

Microsoft Entra application proxy is a service provided in paid SKUs of Microsoft Entra ID that allow users to connect to internal applications through Azure's own reverse-proxy service. This allows the RD Web and RD Gateway endpoints to be hidden inside of the virtual network, eliminating the need to be exposed to the internet by a public IP address. Hosters can use Microsoft Entra application proxy to condense the number of virtual machines in the tenant's environment while still maintaining a full deployment. Microsoft Entra application proxy also enables many of the benefits that Microsoft Entra ID provides, such as conditional access and multi-factor authentication.

For more information, see [Get started with Application Proxy and install the connector](/en-us/azure/active-directory/manage-apps/application-proxy-enable).