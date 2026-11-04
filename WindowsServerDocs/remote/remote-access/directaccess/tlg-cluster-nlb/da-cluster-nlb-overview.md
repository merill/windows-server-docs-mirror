---
layout: Conceptual
title: Overview of the DirectAccess Cluster-NLB Test Lab Scenario | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-cluster-nlb/da-cluster-nlb-overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn about the DirectAccess Cluster-NLB test lab Scenario and the three subnets it consists of.
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 546d29b7-1f9c-11a0-fb8f-44a78f6f21e1
document_version_independent_id: b78e77c4-d2e9-bdd7-4a43-d9853fe8a744
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-cluster-nlb/da-cluster-nlb-overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-cluster-nlb/da-cluster-nlb-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-cluster-nlb/da-cluster-nlb-overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: eac5835a-fdb1-fac8-e9fb-b159ea264096
---

# Overview of the DirectAccess Cluster-NLB Test Lab Scenario | Microsoft Learn

In this test lab scenario, DirectAccess is deployed with:

- **DC1**-A server that is configured as a domain controller, Domain Name System (DNS) server, and Dynamic Host Configuration Protocol (DHCP) server.
- **EDGE1**-A server on the internal network that is configured as the first Remote Access server in a Remote Access server cluster. This server has two network adapters; one connected to the internal network, and the other connected to the external network.
- **EDGE2**-A server on the internal network that is configured as the second Remote Access server in a Remote Access server cluster. This server has two network adapters; one connected to the internal network, and the other connected to the external network.
- **APP1**-A server on the internal network that is configured as a web and file server, and as an enterprise root certification authority (CA)
- **APP2**-A computer on the internal network that is configured as an IPv4 only web and file server. This computer is used to highlight the NAT64/DNS64 capabilities.
- **INET1**-A server that is configured as an Internet DNS and DHCP server.
- **NAT1**-A client computer that is configured as a network address translator (NAT) device using Internet Connection Sharing.
- **CLIENT1**-A client computer that is configured as a DirectAccess client that will be used to test DirectAccess connectivity when moving between the internal network, the simulated Internet, and a home network.

The test lab consists of three subnets that simulate the following:

- A home network named Homenet (192.168.137.0/24) connected to the Internet by a NAT.
- The external network represented by the Internet subnet (131.107.0.0/24).
- An internal network named Corpnet (10.0.0.0/24; 2001:db8:1::/64) separated from the Internet by the Remote Access server.

Computers on each subnet connect using either a physical or virtual hub or switch, as shown in the following figure.

![Test lab overview](../../../media/overview-of-the-test-lab-scenario_5/tlg_da_cluster.png)