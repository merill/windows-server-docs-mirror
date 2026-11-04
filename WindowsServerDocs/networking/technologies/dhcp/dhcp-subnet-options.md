---
layout: Conceptual
title: DHCP Subnet Selection Options | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/dhcp/dhcp-subnet-options
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides information about DHCP subnet selection options for Dynamic Host Configuration Protocol (DHCP) in Windows Server 2016.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2018-08-17T00:00:00.0000000Z
locale: en-us
document_id: 58c9a735-22a3-4123-e386-407f49a19bbd
document_version_independent_id: e1704867-4a1c-8446-52da-ecd07ddc35d7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/dhcp/dhcp-subnet-options.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/dhcp/dhcp-subnet-options
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/dhcp/dhcp-subnet-options.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 1cc5302e-a7fa-3ac9-9814-f3769588be66
---

# DHCP Subnet Selection Options | Microsoft Learn

You can use this topic for information about new DHCP subnet selection options.

DHCP now supports option 82 (sub-option 5). You can use these options to allow DHCP proxy clients and relay agents to request an IP address for a specific subnet, and from a specific IP address range and scope. For more details, see **Option 82 Sub Option 5**: [RFC 3527 Link Selection sub-option for the Relay Agent Information Option for DHCPv4](https://tools.ietf.org/html/rfc3527).

If you are using a DHCP relay agent that is configured with DHCP option 82, sub-option 5, the relay agent can request an IP address lease for DHCP clients from a specific IP address range.

## Option 82 Sub Option 5: Link Selection Sub Option

The Relay Agent Link Selection sub-option allows a DHCP Relay Agent to specify an IP subnet from which the DHCP server should assign IP addresses and options.

Typically, DHCP relay agents rely on the Gateway IP Address (GIADDR) field to communicate with DHCP servers. However, GIADDR is limited by its two operational functions:

1. To inform the DHCP server about the subnet upon which the DHCP client that is requesting the IP address lease resides.
2. To inform the DHCP server of the IP address to use to communicate with the relay agent.

In some cases, the IP address that the relay agent uses to communicate with the DHCP server might be different than the IP address range from which the DHCP client IP address needs to be allocated.

The Link Selection Sub option of option 82 is useful in this situation, allowing the relay agent to explicitly state the subnet from which it wants the IP address allocated in the form of DHCP v4 option 82 sub option 5.

Note

All relay agent IP addresses (GIADDR) must be part of an active DHCP scope IP address range. Any GIADDR outside of the DHCP scope IP address ranges is considered a rogue relay and Windows DHCP Server will not acknowledge DHCP client requests from those relay agents.

A special scope can be created to "authorize" relay agents. Create a scope with the GIADDR (or multiple if the GIADDR's are sequential IP addresses), exclude the GIADDR address(es) from distribution, and then activate the scope. This will authorize the relay agents while preventing the GIADDR addresses from being assigned.

### Use case scenario

In this scenario, an organization network includes both a DHCP server and a Wireless Access Point (AP) for the guest users. Guests client IP addresses are assigned from the organization DHCP server - however, due to firewall policy restrictions, the DHCP server cannot access the guest wireless network or wireless clients with broadcase messages.

To resolve this restriction, the AP is configured with the Link Selection Sub Option 5 to specify the subnet from which it wants the IP address allocated for guest clients, while in the GIADDR also specifying the IP address of the internal interface that leads to the corporate network.