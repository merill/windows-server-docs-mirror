---
layout: Conceptual
title: Creating a Site Link Bridge Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/creating-a-site-link-bridge-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Creating a Site Link Bridge Design'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 028cd4f3-4e39-9b7e-5dc8-33dbd8e7b3ca
document_version_independent_id: d6a1ec63-dc3c-ff96-5597-ed6ee0e4e73e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Creating-a-Site-Link-Bridge-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/creating-a-site-link-bridge-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Creating-a-Site-Link-Bridge-Design.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 4eff14d1-7ffb-4137-7ab8-8e8e25cb689a
---

# Creating a Site Link Bridge Design | Microsoft Learn

A site link bridge connects two or more site links and enables transitivity between site links. Each site link in a bridge must have a site in common with another site link in the bridge. The Knowledge Consistency Checker (KCC) uses the information on each site link to compute the cost of replication between sites in one site link and sites in the other site links of the bridge. Without the presence of a common site between site links, the KCC also cannot establish direct connections between domain controllers in the sites that are connected by the same site link bridge.

By default, all site links are transitive. We recommend that you keep transitivity enabled by not changing the default value of **Bridge all site links** (enabled by default). However, you will need to disable **Bridge all site links** and complete a site link bridge design if:

- Your IP network is not fully routed. When you disable **Bridge all site links**, all site links are considered nontransitive, and you can create and configure site link bridge objects to model the actual routing behavior of your network.
- You need to control the replication flow of the changes made in Active Directory Domain Services (AD DS). By disabling **Bridge all site links** for the site link IP transport and configuring a site link bridge, the site link bridge becomes the equivalent of a disjointed network. All site links within the site link bridge can route transitively, but they do not route outside of the site link bridge.

For more information about how to use the Active Directory Sites and Services snap-in to disable the **Bridge all site links** setting, see the article [Enable or disable site link bridges](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc738789%28v=ws.10%29).

## Controlling AD DS replication flow

Two scenarios in which you need a site link bridge design to control replication flow include controlling replication failover and controlling replication through a firewall.

### Controlling replication failover

If your organization has a hub-and-spoke network topology, you generally do not want the satellite sites to create replication connections to other satellite sites if all domain controllers in the hub site fail. In such scenarios, you must disable **Bridge all site links** and create site link bridges so that replication connections are created between the satellite site and another hub site that is just one or two hops away from the satellite site.

### Controlling replication through a firewall

If two domain controllers representing the same domain in two different sites are specifically allowed to communicate with each other only through a firewall, you can disable **Bridge all site links** and create site link bridges for sites on the same side of the firewall. Therefore, if your network is separated by firewalls, we recommend that you disable transitivity of site links and create site link bridges for the network on one side of the firewall.