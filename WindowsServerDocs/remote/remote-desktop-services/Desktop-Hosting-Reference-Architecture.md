---
layout: Conceptual
title: Desktop Hosting Reference Architecture | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/desktop-hosting-reference-architecture
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Architectural guidance for creating a desktop hosting solution with RDS and Azure.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: reference-architecture
author: robinharwood
locale: en-us
document_id: af3af572-0c64-c47a-cb5d-8719ddd3d01d
document_version_independent_id: e71f54c2-49d8-4cf8-5752-a5470b105e1a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/Desktop-Hosting-Reference-Architecture.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/desktop-hosting-reference-architecture
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/Desktop-Hosting-Reference-Architecture.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 85df40be-99b7-760b-cd67-52fb08307e59
---

# Desktop Hosting Reference Architecture | Microsoft Learn

This article defines a set of architectural blocks for using Remote Desktop Services (RDS) and Microsoft Azure virtual machines to create multitenant, hosted Windows desktop and application services, which we call "desktop hosting." You can use this architecture reference to create highly secure, scalable, and reliable desktop hosting solutions for small- and medium-sized organizations with 5 to 5000 users.

The primary audience for this reference architecture is hosting providers who want to leverage Microsoft Azure Infrastructure Services to deliver desktop hosting services and Subscriber Access Licenses (SALs) to multiple tenants via the [Microsoft Service Provider Licensing Agreement](https://www.microsoft.com/hosting/en/us/licensing/splabenefits.aspx) (SPLA) program. A second audience for this reference architecture are end customers who want to create and manage desktop hosting solutions in Microsoft Azure Infrastructure Services for their own employees using [RDS User CALs extended rights through Software Assurance](https://download.microsoft.com/download/6/B/A/6BA3215A-C8B5-4AD1-AA8E-6C93606A4CFB/Windows_Server_2012_R2_Remote_Desktop_Services_Licensing_Datasheet.pdf) (SA).

To deliver a desktop hosting solutions, hosting partners and SA customers leverage Windows Server to deliver Windows users an application experience that is familiar to business users and consumers. Built on the foundations of Windows 10, Windows Server 2016 provides familiar application support and user experience.

The scope of this document is limited to:

- Architectural design guidance for a desktop hosting service. Detailed information, such as deployment procedures, performance, and capacity planning is explained in separate documents. For more general information about Azure Infrastructure Services, see [Virtual Machines in Azure](/en-us/azure/virtual-machines/).
- Session-based desktops, RemoteApp applications, and server-based personal desktops that use Windows Server 2016 Remote Desktop Session Host (RD Session Host). Windows client-based virtual desktop infrastructures aren't covered because there's no Service Provider License Agreement (SPLA) for Windows client operating systems. Windows Server-based virtual desktop infrastructures are allowed under the SPLA, and Windows client-based virtual desktop infrastructures are allowed on dedicated hardware with end-customer licenses in certain scenarios. However, client-based virtual desktop infrastructures are out-of-scope for this document.
- Microsoft products and features, primarily Windows Server 2016 and Microsoft Azure Infrastructure Services.
- Desktop hosting services for tenants ranging in size from 5 to 5000 users. For larger tenants, you may need to modify this architecture to provide adequate performance. The Server Manager RDS graphical user interface (GUI) isn't recommended for deployments over 500 users. PowerShell is recommended for managing RDS deployments between 500 and 5000 users.
- The minimum set of components and services required for a desktop hosting service. There are many optional components and services that can be added to enhance a desktop hosting service, but these are out-of-scope for this document.

After reading this document, the reader should understand:

- The building blocks for providing a secure, reliable, multitenant desktop hosting solution based in Microsoft Azure Services.
- The purpose of each building block and how they fit together.

There are multiple ways to build a desktop hosting solution based on this architecture. This architecture outlines integration and improvements in Azure with Windows Server 2016. Other deployment options are available with the [Desktop Hosting Reference Architecture Guide](https://go.microsoft.com/fwlink/p/?LinkId=517389).

The following topics are covered:

- [Desktop hosting logical architecture](desktop-hosting-logical-architecture)
- [Understand the RDS Roles](desktop-hosting-service)
- [Understand the desktop hosting environment](understanding-the-desktop-hosting-environment)
- [Azure services and considerations for desktop hosting](azure-services-and-considerations-for-desktop-hosting)