---
layout: Conceptual
title: Configure NPS UDP Port Information | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-udp-ports-configure
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: You can use this topic to configure the ports that Network Policy Server (NPS) uses for Remote Authentication Dial-In User Service (RADIUS) authentication and accounting traffic in Windows Server 2016.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 9671f5de-f066-6ece-5762-681ad144a6a2
document_version_independent_id: 308f05d0-f6f0-1c7b-2c27-a2212a4f66ee
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-udp-ports-configure.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-udp-ports-configure
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-udp-ports-configure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 7b06b17d-99d5-33b0-bd05-4823149b5452
---

# Configure NPS UDP Port Information | Microsoft Learn

You can use the following procedure to configure the ports that Network Policy Server (NPS) uses for Remote Authentication Dial-In User Service (RADIUS) authentication and accounting traffic.

By default, NPS listens for RADIUS traffic on ports 1812, 1813, 1645, and 1646 for both Internet Protocol version 6 (IPv6) and IPv4 for all installed network adapters.

Note

If you uninstall either IPv4 or IPv6 on a network adapter, NPS does not monitor RADIUS traffic for the uninstalled protocol.

The port values of 1812 for authentication and 1813 for accounting are RADIUS standard ports defined by the Internet Engineering Task Force (IETF) in RFCs 2865 and 2866. However, by default, many access servers use ports 1645 for authentication requests and 1646 for accounting requests. No matter which port numbers you decide to use, make sure that NPS and your access server are configured to use the same ones.

> 
> [IMPORTANT] If you do not use the RADIUS default port numbers, you must configure exceptions on the firewall for the local computer to allow RADIUS traffic on the new ports. For more information, see [Configure Firewalls for RADIUS Traffic](nps-firewalls-configure).

Membership in **Domain Admins**, or equivalent, is the minimum required to complete this procedure.

## To configure NPS UDP port information

1. Open the NPS console.
2. Right-click **Network Policy Server**, and then click **Properties**.
3. Click the **Ports** tab, and then examine the settings for ports. If your RADIUS authentication and RADIUS accounting UDP ports vary from the default values provided (1812 and 1645 for authentication, and 1813 and 1646 for accounting), type your port settings in **Authentication** and **Accounting**.
4. To use multiple port settings for authentication or accounting requests, separate the port numbers with commas.

For more information about managing NPS, see [Manage Network Policy Server](nps-manage-top).

For more information about NPS, see [Network Policy Server (NPS)](nps-top).