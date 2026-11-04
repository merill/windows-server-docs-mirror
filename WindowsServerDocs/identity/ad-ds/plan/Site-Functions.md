---
layout: Conceptual
title: Site functions | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/site-functions
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn more about various site functions in AD DS
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 0e93bc1e-7c49-eb05-582b-fe415eec6eda
document_version_independent_id: 56716e83-0d0d-efde-5898-b1868f7ad078
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Site-Functions.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/site-functions
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Site-Functions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: f85711b5-0a10-7f46-ac2a-2d6d3ad7672d
---

# Site functions | Microsoft Learn

Windows Server 2008 uses site information for many purposes, including routing replication, client affinity, system volume (SYSVOL) replication, Distributed File System Namespaces (DFSN), and service location.

## Routing replication

Active Directory Domain Services (AD DS) uses a multimaster, store-and-forward method of replication. A domain controller communicates directory changes to a second domain controller, which then communicates to a third, and so on, until all domain controllers have received the change. To achieve the best balance between reducing replication latency and reducing traffic, site topology controls Active Directory replication by distinguishing between replication that occurs within a site and replication that occurs between sites.

Within sites, replication is optimized for speed, data updates trigger replication, and the data is sent without the overhead required by data compression. Conversely, replication between sites is compressed to minimize the cost of transmission over wide area network (WAN) links. When replication occurs between sites, a single domain controller per domain at each site collects and stores the directory changes and communicates them at a scheduled time to a domain controller in another site.

## Client affinity

Domain controllers use site information to inform Active Directory clients about domain controllers present within the closest site as the client. For example, consider a client in the Seattle site that doesn't know its site affiliation and contacts a domain controller from the Atlanta site. Based on the IP address of the client, the domain controller in Atlanta determines which site the client is actually from and sends the site information back to the client. The domain controller also informs the client whether the chosen domain controller is the closest one to it. The client caches the site information provided by the domain controller in Atlanta, queries for the site-specific service (SRV) resource record (a Domain Name System (DNS) resource record used to locate domain controllers for AD DS) and thereby finds a domain controller within the same site.

By finding a domain controller in the same site, the client avoids communications over WAN links. If no domain controllers are located at the client site, a domain controller that has the lowest cost connections relative to other connected sites advertises itself (registers a site-specific service (SRV) resource record in DNS) in the site that doesn't have a domain controller. The domain controllers that are published in DNS are those from the closest site as defined by the site topology. This process ensures that every site has a preferred domain controller for authentication.

For more information about the process of locating a domain controller, see [Active Directory Collection](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc780036%28v=ws.10%29).

## SYSVOL replication

SYSVOL is a collection of folders in the file system that exists on each domain controller in a domain. The SYSVOL folders provide a default Active Directory location for files that must be replicated throughout a domain, including Group Policy objects (GPOs), startup and shutdown scripts, and logon and logoff scripts. Windows Server 2008 can use the File Replication Service (FRS) or Distributed File System Replication (DFSR) to replicate changes made to the SYSVOL folders from one domain controller to other domain controllers. FRS and DFSR replicate these changes according to the schedule that you create during your site topology design.

## DFSN

DFSN uses site information to direct a client to the server that's hosting the requested data within the site. If DFSN doesn't find a copy of the data within the same site as the client, DFSN uses the site information in AD DS to determine which file server that has DFSN shared data is closest to the client.

## Service location

By publishing services such as file and print services in AD DS, you allow Active Directory clients to locate the requested service within the same or nearest site. Print services use the location attribute stored in AD DS to let users browse for printers by location without knowing their precise location. For more information about designing and deploying print servers, see [Designing and Deploying Print Servers](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc785842%28v=ws.10%29).