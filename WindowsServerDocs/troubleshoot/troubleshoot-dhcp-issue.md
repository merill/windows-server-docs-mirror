---
layout: Conceptual
title: Troubleshooting guide for Dynamic Host Configuration Protocol (DHCP) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/troubleshoot/troubleshoot-dhcp-issue
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: troubleshoot
ms.update-cycle: 1095-days
description: This article introduces a troubleshooting guide for DHCP issues.
ms.date: 2020-05-26T00:00:00.0000000Z
ms.topic: troubleshooting
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: d1cc607e-4f20-b719-ed4f-97fcb3b21feb
document_version_independent_id: 7a08238f-e236-9388-b072-715d63ec3163
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/troubleshoot/troubleshoot-dhcp-issue.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../networking/toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: troubleshoot/troubleshoot-dhcp-issue
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/troubleshoot/troubleshoot-dhcp-issue.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e2181536-cc79-043d-de19-0ef50f143d66
---

# Troubleshooting guide for Dynamic Host Configuration Protocol (DHCP) | Microsoft Learn

For any device (such as a computer or phone) to be able to operate in a network, it must be assigned an IP address. You can assign an IP address manually or automatically. The automatic assignment is handled by the DHCP service (Microsoft or third-party server).

In this article, we will discuss general troubleshooting steps for the Microsoft IPv4 DHCP client and server.

## More information

The procedure for IPv4 address assignment usually involves three main components:

- A DHCP client device that has to obtain an IP address
- A DHCP service that provides IP addresses to the client based on specific settings
- A DHCP relay agent /IP Helper to send DHCP broadcast requests to a different network segment

A DHCP client-to-server communication consists of three kinds of interaction between the two peers:

- **Broadcast-based DORA** (Discover, Offer, Request, Acknowledgement). This process consists of the following steps:

    - The DHCP client sends a DHCP Discover broadcast request to all available DHCP servers within range.
    - A DHCP Offer broadcast response is received from the DHCP server, offering an available IP address lease.
    - The DHCP client broadcast Request asks for the offered IP address lease and the DHCP broadcast Acknowledgement at the end.
    - If the DHCP client and server are located in different logical network segments, a DHCP relay agent acts a forwarder, sending the DHCP broadcast packets back and forth between peers.
- **Unicast DHCP Renew requests**: These are sent directly to the DHCP server from the DHCP client to renew the IP address assignment after 50 percent of the IP address lease time.
- **Rebind DHCP broadcast requests**: These are made to any DHCP server within range of the client. These are sent after 87.5 percent of the IP address lease duration because this indicates that the directed unicast request didn’t work. As for the DORA process, this process involves a DHCP relay agent communication.

If a Microsoft DHCP client does not receive a valid DHCP IPv4 address, the client is likely configured to use an APIPA address. For more information, see the following Knowledge Base article: [220874](https://support.microsoft.com/help/220874) How to use automatic TCP/IP addressing without a DHCP server

All communication is done on UDP ports 67 and 68. For more information, see the following Knowledge Base article: [169289](https://support.microsoft.com/help/169289) DHCP (Dynamic Host Configuration Protocol) Basics.