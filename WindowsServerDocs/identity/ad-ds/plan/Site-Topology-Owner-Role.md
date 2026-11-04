---
layout: Conceptual
title: Site Topology Owner Role | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/site-topology-owner-role
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Site Topology Owner Role'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: c5d4ed50-2e55-fefe-316b-bb15a07c1021
document_version_independent_id: 0aea51cd-0c3a-cd8b-28c6-3d54d8f9bf6f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Site-Topology-Owner-Role.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/site-topology-owner-role
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Site-Topology-Owner-Role.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 14edad3b-5d42-89cb-7abb-c9350eda5002
---

# Site Topology Owner Role | Microsoft Learn

The administrator who manages the site topology is known as the site topology owner. The site topology owner understands the conditions of the network between sites and has the authority to change settings in Active Directory Domain Services (AD DS) to implement changes to the site topology. Changes to the site topology affect changes in the replication topology. The site topology owner's responsibilities include:

- Controlling changes to the site topology if network connectivity changes.
- Obtaining and maintaining information about network connections and routers from the network group. The site topology owner must maintain a list of subnet addresses, subnet masks, and the location to which each belongs. The site topology owner must also understand any issues about network speed and capacity that affect site topology to effectively set costs for site links.
- Moving Active Directory server objects representing domain controllers between sites if a domain controller's IP address changes to a different subnet in a different site, or if the subnet itself is assigned to a different site. In either case, the site topology owner must manually move the Active Directory server object of the domain controller to the new site.