---
layout: Conceptual
title: Overview of the Test Lab Scenario | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-multisite/overview-of-the-test-lab-scenario_4
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn about what DirectAccess is deployed with and the four subnets that make up the the test lab.
ms.topic: tutorial
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 18fc2e26-1e74-e227-e4fd-de16952598d1
document_version_independent_id: 2fb9eed7-6c4b-9063-9048-f6ec948ef825
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/Overview-of-the-Test-Lab-Scenario_4.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-multisite/overview-of-the-test-lab-scenario_4
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/Overview-of-the-Test-Lab-Scenario_4.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/7352ca82-c945-4fdf-9a72-119b613f0175
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/04aed1aa-867d-41c7-836d-36bdb27db265
platformId: c9585bd0-83d7-758b-178a-1d064d7fb7eb
---

# Overview of the Test Lab Scenario | Microsoft Learn

In this test lab scenario, DirectAccess is deployed with:

- **DC1**-A server that is configured as a domain controller, DNS server, and DHCP server for the corp.contoso.com domain.
- **2-DC1**-A server that is configured as a domain controller and DNS server for the corp2.corp.contoso.com domain.
- **EDGE1 and 2-EDGE1**-Two servers on the internal network that are configured as Remote Access servers. Each server has two network adapters; one connected to the internal network, and the other connected to the external network.
- **APP1 and 2-APP1**-Two servers on the internal network that are configured as web and file servers.
- **APP2**-A computer on the internal network that is configured as an IPv4 only web and file server. This computer is used to highlight the NAT64/DNS64 capabilities.
- **ROUTER1**-A server that is configured to provide routing between the two corporate internal networks.
- **INET1**-A server that is configured as an Internet DNS and DHCP server.
- **NAT1**-A client computer that is configured as a network address translator (NAT) device using Internet Connection Sharing.
- **CLIENT1 and CLIENT2**-Two client computers that are configured as DirectAccess clients that will be used to test DirectAccess connectivity when moving between the internal network, the simulated Internet, and a home network. **CLIENT2** is a Windows 7® client.

The test lab consists of four subnets that simulate the following:

- A home network named Homenet (192.168.137.0/24) connected to the Internet by a NAT.
- The external network represented by the Internet subnet (131.107.0.0/24).
- An internal network named Corpnet (10.0.0.0/24; 2001:db8:1::/64) separated from the Internet by the EDGE1 Remote Access server.
- An internal network named 2-Corpnet1 (10.2.0.0/24; 2001:db8:2::/64) separated from the Internet by the 2-EDGE1 Remote Access server.

Computers on each subnet connect using either a physical or virtual hub or switch, as shown in the following figure.

![Test lab overview](../../../media/overview-of-the-test-lab-scenario_4/tlg_da_multisite.png)