---
layout: Conceptual
title: Creating a Site Link Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/creating-a-site-link-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Creating a Site Link Design'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 203bd71d-7ec0-3141-04eb-2392bf00a60c
document_version_independent_id: b79078f7-297f-8935-72e1-c212d8961b80
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Creating-a-Site-Link-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/creating-a-site-link-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Creating-a-Site-Link-Design.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 47f647ce-7849-fe27-555f-693ea5613697
---

# Creating a Site Link Design | Microsoft Learn

Create a site link design to connect your sites with site links. Site links reflect the intersite connectivity and method used to transfer replication traffic. You must connect sites with site links so that domain controllers at each site can replicate Active Directory changes.

## Connecting sites with site links

To connect sites with site links, identify the member sites that you want to connect with the site link, create a site link object in the respective Inter-Site Transports container, and then name the site link. After you create the site link, you can proceed to set the site link properties.

When creating site links, ensure that every site is included in a site link. In addition, ensure that all sites are connected to each other through other site links so that the changes can be replicated from domain controllers in any site to all other sites. If you fail to do this, an error message is generated in the Directory Service log in Event Viewer stating that the site topology is not connected.

Whenever you add sites to a newly created site link, determine if the site being added is a member of other site links, and change the site link membership of the site if needed. For example, if you make a site a member of the Default-First-Site-Link when you initially create the site, be sure to remove the site from the Default-First-Site-Link after you add the site to a new site link. If you do not remove the site from the Default-First-Site-Link, the Knowledge Consistency Checker (KCC) will make routing decisions based on the membership of both site links, which may result in incorrect routing.

To identify the member sites that you want to connect with a site link, use the list of locations and linked locations that you recorded in the "Geographic Locations and Communication Links" (DSSTOPO\_1.doc) worksheet. If multiple sites have the same connectivity and availability to each other, you can connect them with the same site link.

The Inter-Site Transports container provides the means for mapping site links to the transport that the link uses. When you create a site link object, you create it in either the IP container, which associates the site link with the remote procedure call (RPC) over IP transport, or the Simple Mail Transfer Protocol (SMTP) container, which associates the site link with the SMTP transport.

Note

SMTP replication will not be supported in future versions of Active Directory Domain Services (AD DS); therefore, creating site links objects in the SMTP container is not recommended.

When you create a site link object in the respective Inter-Site Transports container, AD DS uses RPC over IP to transfer both intersite and intrasite replication between domain controllers. To keep data secure while in transit, RPC over IP replication uses both the Kerberos authentication protocol and data encryption.

When a direct IP connection is not available, you can configure replication between sites to use SMTP. However, SMTP replication functionality is limited and requires an enterprise certification authority (CA). SMTP can only replicate the configuration, schema, and application directory partitions and does not support the replication of domain directory partitions.

To name site links, use a consistent naming scheme, such as name\_of\_site1-name\_of\_site2. Record the list of sites, linked sites, and the names of the site links connecting these sites in a worksheet. For a worksheet to assist you in recording site names and associated site link names, see [Job Aids for Windows Server 2003 Deployment Kit](https://microsoft.com/download/details.aspx?id=9608), download Job\_Aids\_Designing\_and\_Deploying\_Directory\_and\_Security\_Services.zip, and open "Sites and Associated Site Links" (DSSTOPO\_5.doc).

## In this guide

[Setting Site Link Properties](setting-site-link-properties)