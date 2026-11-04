---
layout: Conceptual
title: Upgrading your Remote Desktop Session Host | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/upgrade-to-rdsh
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to upgrade your existing Remote Desktop Session Host.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: upgrade-and-migration-article
author: robinharwood
locale: en-us
document_id: e92d7cfd-0093-04f9-0fe5-c0b4acf86e77
document_version_independent_id: 2d287dfe-4b63-b940-89b8-f6e0d061f85f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/upgrade-to-rdsh.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/upgrade-to-rdsh
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/upgrade-to-rdsh.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 9e487a82-9d87-6143-b334-4cb03360fcfa
---

# Upgrading your Remote Desktop Session Host | Microsoft Learn

Important

All applications must be uninstalled before the upgrade and reinstalled after the upgrade to avoid any app compatibility issues that may rise because of the upgrade.

## Upgrading a RDS session-based collection

In order to keep the down-time to a minimum, it's best to follow these steps while upgrading a RDS session-based collection:

1. Identify the servers to be upgraded, say, half the servers in the collection.
2. Prevent new connections to these servers by setting **Allow New Connections** to false.
3. Log off all sessions on these servers.
4. Remove these servers from the collection.
5. Upgrade the servers to the latest Windows Server version.
6. Set **Allow New Connections** to "false" on the remaining servers in the collection.
7. Add the upgraded servers back to their corresponding collections.
8. Remove the remaining set of servers to be upgraded from the collection.
9. Set **Allow New Connections** to "true" on the upgraded servers in the collection.
10. Upgrade the remaining servers in the deployment by following steps 3 through 9.

## Upgrading a standalone RD Session Host server

A standalone RD Session Host server can be upgraded anytime.