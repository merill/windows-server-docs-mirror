---
layout: Conceptual
title: Configure Connection Request Policies | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/nps/nps-crp-configure
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides information on how to configure Connection Request Policies in Network Policy Server in Windows Server 2016.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 29eb6679-43d7-8fe1-1359-bf88a25a2d1f
document_version_independent_id: 9d77eb43-6cc2-44e1-4838-587b1c622478
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/nps/nps-crp-configure.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/nps/nps-crp-configure
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/nps/nps-crp-configure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d6129e01-1134-8cd1-7acd-8662fc5f8387
---

# Configure Connection Request Policies | Microsoft Learn

You can use this topic to create and configure connection request policies that designate whether the local NPS processes connection requests or forwards them to remote RADIUS server for processing.

Connection request policies are sets of conditions and settings that allow network administrators to designate which Remote Authentication Dial-In User Service (RADIUS) servers perform the authentication and authorization of connection requests that the server running Network Policy Server (NPS) receives from RADIUS clients.

The default connection request policy uses NPS as a RADIUS server and processes all authentication requests locally.

To configure a server running NPS to act as a RADIUS proxy and forward connection requests to other NPS or RADIUS servers, you must configure a remote RADIUS server group in addition to adding a new connection request policy that specifies conditions and settings that the connection requests must match.

You can create a new remote RADIUS server group while you are creating a new connection request policy with the New Connection Request Policy Wizard.

If you do not want the NPS to act as a RADIUS server and process connection requests locally, you can delete the default connection request policy.

If you want the NPS to act as both a RADIUS server, processing connection requests locally, and as a RADIUS proxy, forwarding some connection requests to a remote RADIUS server group, add a new policy using the following procedure and then verify that the default connection request policy is the last policy processed by placing it last in the list of policies.

## Add a Connection Request Policy

Membership in **Domain Admins**, or equivalent, is the minimum required to complete this procedure.

### To add a new connection request policy

1. In Server Manager, click **Tools**, and then click **Network Policy Server** to open the NPS console.
2. In the console tree, double-click **Policies**.
3. Right-click **Connection Request Policies**, and then click **New Connection Request Policy**.
4. Use the New Connection Request Policy Wizard to configure your connection request policy and, if not previously configured, a remote RADIUS server group.

For more information about managing NPS, see [Manage Network Policy Server](nps-manage-top).

For more information about NPS, see [Network Policy Server (NPS)](nps-top).