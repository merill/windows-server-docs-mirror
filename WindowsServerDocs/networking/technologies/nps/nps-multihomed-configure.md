---
layout: Conceptual
title: Configure NPS on a Multihomed Computer | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-multihomed-configure
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides instructions on configuring a server with multiple network adapters that is running Network Policy Server in Windows Server 2016.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: cfd51bb1-26e7-89cd-c538-4f71c4653385
document_version_independent_id: 119a4fc0-d9c6-b4bb-796b-21cee76f5b42
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-multihomed-configure.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-multihomed-configure
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-multihomed-configure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 11b41398-938b-9386-2470-65d3ceb3d70d
---

# Configure NPS on a Multihomed Computer | Microsoft Learn

You can use this topic to configure an NPS with multiple network adapters.

When you use multiple network adapters in a server running Network Policy Server (NPS), you can configure the following:

- The network adapters that do and do not send and receive Remote Authentication Dial-In User Service (RADIUS) traffic.
- On a per-network adapter basis, whether NPS monitors RADIUS traffic on Internet Protocol version 4 (IPv4), IPv6, or both IPv4 and IPv6.
- The UDP port numbers over which RADIUS traffic is sent and received on a per-protocol (IPv4 or IPv6), per-network adapter basis.

By default, NPS listens for RADIUS traffic on ports 1812, 1813, 1645, and 1646 for both IPv6 and IPv4 for all installed network adapters. Because NPS automatically uses all network adapters for RADIUS traffic, you only need to specify the network adapters that you want NPS to use for RADIUS traffic when you want to prevent NPS from using a specific network adapter.

Note

If you uninstall either IPv4 or IPv6 on a network adapter, NPS does not monitor RADIUS traffic for the uninstalled protocol.

On an NPS that has multiple network adapters installed, you might want to configure NPS to send and receive RADIUS traffic only on the adapters you specify.

For example, one network adapter installed in the NPS might lead to a network segment that does not contain RADIUS clients, while a second network adapter provides NPS with a network path to its configured RADIUS clients. In this scenario, it is important to direct NPS to use the second network adapter for all RADIUS traffic.

In another example, if your NPS has three network adapters installed, but you only want NPS to use two of the adapters for RADIUS traffic, you can configure port information for the two adapters only. By excluding port configuration for the third adapter, you prevent NPS from using the adapter for RADIUS traffic.

## Using a network adapter

To configure NPS to listen for and send RADIUS traffic on a network adapter, use the following syntax on the Properties dialog box of Network Policy Server in the NPS console:

- IPv4 traffic syntax: IPAddress:UDPport , where IPAddress is the IPv4 address that is configured on the network adapter over which you want to send RADIUS traffic, and UDPport is the RADIUS port number that you want to use for RADIUS authentication or accounting traffic.
- IPv6 traffic syntax: [IPv6Address] : UDPport , where the brackets around IPv6Address are required, IPv6Address is the IPv6 address that is configured on the network adapter over which you want to send RADIUS traffic, and UDPport is the RADIUS port number that you want to use for RADIUS authentication or accounting traffic.

The following characters can be used as delimiters for configuring IP address and UDP port information:

- Address/port delimiter: colon (:)
- Port delimiter: comma (,)
- Interface delimiter: semicolon (;)

## Configuring network access servers

Make sure that your network access servers are configured with the same RADIUS UDP port numbers that you configure on your NPSs. The RADIUS standard UDP ports defined in RFCs 2865 and 2866 are 1812 for authentication and 1813 for accounting; however, some access servers are configured by default to use UDP port 1645 for authentication requests and UDP port 1646 for accounting requests.

Important

If you do not use the RADIUS default port numbers, you must configure exceptions on the firewall for the local computer to allow RADIUS traffic on the new ports. For more information, see [Configure Firewalls for RADIUS Traffic](nps-firewalls-configure).

## Configure the multihomed NPS

You can use the following procedure to configure your multihomed NPS.

Membership in **Domain Admins**, or equivalent, is the minimum required to complete this procedure.

### To specify the network adapter and UDP ports that NPS uses for RADIUS traffic

1. In Server manager, click **Tools**, and then click **Network Policy Server** to open the NPS console.
2. Right-click **Network Policy Server**, and then click **Properties**.
3. Click the **Ports** tab, and prepend the IP address for the network adapter you want to use for RADIUS traffic to the existing port numbers. For example, if you want to use the IP address 192.168.1.2 and RADIUS ports 1812 and 1645 for authentication requests, change the port setting from **1812,1645** to **192.168.1.2:1812,1645**. If your RADIUS authentication and RADIUS accounting UDP ports are different from the default values, change the port settings accordingly.
4. To use multiple port settings for authentication or accounting requests, separate the port numbers with commas.

For more information about NPS UDP ports, see [Configure NPS UDP Port Information](nps-udp-ports-configure)

For more information about NPS, see [Network Policy Server](nps-top)