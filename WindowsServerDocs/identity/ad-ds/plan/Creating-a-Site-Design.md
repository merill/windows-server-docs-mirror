---
layout: Conceptual
title: Creating a Site Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/creating-a-site-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Creating a Site Design'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 6b6541ec-7b0b-b85f-9e32-9751e55d0520
document_version_independent_id: eb69ccaf-c07f-9b51-b7ae-6832bf78536e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Creating-a-Site-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/creating-a-site-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Creating-a-Site-Design.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e38b2b16-3600-cab4-7dfb-9f8d95fd640d
---

# Creating a Site Design | Microsoft Learn

Creating a site design involves deciding which locations will become sites, creating site objects, creating subnet objects, and associating the subnets with sites.

## Deciding which locations will become sites

Decide which locations to create sites for as follows:

- Create sites for all locations in which you plan to place domain controllers. Refer to the information documented in the "Domain Controller Placement" (DSSTOPO\_4.doc) worksheet to identify locations that include domain controllers.
- Create sites for those locations that include servers that are running applications that require a site to be created. Certain applications, such as Distributed File System Namespaces (DFSN), use site objects to locate the closest servers to clients.

Note

If your organization has multiple networks in close proximity with fast, reliable connections, you can include all of the subnets for those networks in a single Active Directory site. For example, if the round-trip return network latency between two servers in different subnets is 10 ms or less, you can include both subnets in the same Active Directory site. If the network latency between the two locations is greater than 10 ms, you should not include the subnets in a single Active Directory site. Even when latency is 10 ms or less, you may elect to deploy separate sites if you want to segment the traffic between sites for Active Directory-based applications.

- If a site is not required for a location, add the subnet of the location to a site for which the location has the maximum wide area network (WAN) speed and available bandwidth.

Document locations that will become sites and the network addresses and subnet masks within each location. For a worksheet to assist you in documenting sites, see [Job Aids for Windows Server 2003 Deployment Kit](https://microsoft.com/download/details.aspx?id=9608), download Job\_Aids\_Designing\_and\_Deploying\_Directory\_and\_Security\_Services.zip, and open "Associating Subnets with Sites" (DSSTOPO\_6.doc).

## Creating a site object design

For every location where you have decided to create sites, plan to create site objects in Active Directory Domain Services (AD DS). Document locations that will become sites in the "Associating Subnets with Sites" worksheet.

For more information about how to create site objects, see the article [Create a Site](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc772304%28v=ws.11%29).

## Creating a subnet object design

For every IP subnet and subnet mask associated with each location, plan to create subnet objects in AD DS representing all the IP addresses within the site.

When creating an Active Directory subnet object, the information about network IP subnet and subnet mask is automatically translated into the network prefix length notation format &lt;IP address&gt;/&lt;prefix length&gt;. For example, the network IP version 4 (IPv4) address 172.16.4.0 with a subnet mask 255.255.252.0 appears as 172.16.4.0/22. In addition to IPv4 addresses, Windows Server 2008 also supports IP version 6 (IPv6) subnet prefixes, for example, 3FFE:FFFF:0:C000::/64. For more information about IP subnets in each location, see the "Locations and Subnets" (DSSTOPO\_2.doc) worksheet in [Collecting Network Information](collecting-network-information) and [Appendix A: Locations and Subnet Prefixes](appendix-a--locations-and-subnet-prefixes).

Associate each subnet object with a site object by referring to the "Associating Subnets with Sites" (DSSTOPO\_6.doc) worksheet in "Deciding Which Locations Will Become Sites" section to determine which subnet is to be associated with which site. Document the Active Directory subnet object associated with each location in the "Associating Subnets with Sites" (DSSTOPO\_6.doc) worksheet.

For more information about how to create subnet objects, see the article [Create a Subnet](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc770372%28v=ws.11%29).