---
layout: Conceptual
title: Remote Desktop Services - Access from anywhere | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-plan-access-from-anywhere
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Planning information for an RD Gateway
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: a11a4f0b-1c7c-5ca7-b6db-1307bfcab2a4
document_version_independent_id: 2e4a63ce-e602-b4af-57d3-7214ad21cae1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-plan-access-from-anywhere.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-plan-access-from-anywhere
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-plan-access-from-anywhere.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 9d1c3cbb-6100-cc59-ef4d-c4d003a8a452
---

# Remote Desktop Services - Access from anywhere | Microsoft Learn

End users can connect to internal network resources securely from outside the corporate firewall through RD Gateway.

Regardless of how you configure the desktops for your end-users, you can easily plug the RD Gateway into the connection flow for a fast, secure connection. For end-users connecting through published feeds, you can configure the RD Gateway property as you configure the overall deployment properties. For end-users connecting through to their desktops without a feed, they can easily add the name of the organization's RD Gateway as a connection property no matter which Remote Desktop client application they use.

The three primary purposes of the RD Gateway, in the order of the connection sequence, are:

1. **Establish an encrypted SSL tunnel between the end-user's device and the RD Gateway Server**: In order to connect through any RD Gateway server, the RD Gateway server must have a certificate installed that the end-user's device recognizes. In testing and proofs of concepts, self-signed certificates can be used, but only publicly trusted certificates from a certificate authority should be used in any production environment.
2. **Authenticate the user into the environment**: The RD Gateway uses the inbox IIS service to perform authentication, and can even utilize the RADIUS protocol to leverage [multi-factor authentication](rds-plan-mfa) solutions such as Azure MFA. Aside from the default policies created, you can create additional RD Resource Authorization Policies (RD RAPs) and RD Connection Authorization Policies (RD CAPs) to more specifically define which users should have access to which resources within the secure environment.
3. **Pass traffic back and forth between the end-user's device and the specified resource**: The RD Gateway continues to perform this task for as long as the connection is established. You can specify different timeout properties on the RD Gateway servers to maintain the security of the environment in case the user walks away from the device.

You can find additional details on the overall architecture of a Remote Desktop Services deployment [in the desktop hosting reference architecture](desktop-hosting-reference-architecture).