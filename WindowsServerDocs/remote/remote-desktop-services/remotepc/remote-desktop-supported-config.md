---
layout: Conceptual
title: Remote Desktop client - supported configuration | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/remotepc/remote-desktop-supported-config
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn which PCs you can and can't access by using supported configurations for Remote Desktop clients.
ms.topic: feature-availability
author: robinharwood
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
locale: en-us
document_id: 537a8e93-789e-bb97-dba6-ef1597e76156
document_version_independent_id: 537a8e93-789e-bb97-dba6-ef1597e76156
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/remotepc/remote-desktop-supported-config.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/remotepc/remote-desktop-supported-config
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/remotepc/remote-desktop-supported-config.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c377b488-d067-7557-c8f3-4e2a27e65854
---

# Remote Desktop client - supported configuration | Microsoft Learn

Learn which PCs you can access by using supported configurations for Remote Desktop clients.

## Supported operating systems for Remote Desktop client connections

You can connect to PCs that run the following Windows operating systems:

- Windows 11 Pro
- Windows 11 Enterprise
- Windows 10 Pro
- Windows 10 Enterprise
- Windows Server 2022
- Windows Server 2019
- Windows Server 2016

Note

Windows SKUs that aren't listed in this section, such as Windows 10 Home, aren't compatible with connecting remotely.

## Supported operating systems for Remote Desktop Gateway, Web Access and RemoteApp

The following operating systems can serve as Remote Desktop Gateway, Web Access, and RemoteApp:

- Windows Server 2022
- Windows Server 2019
- Windows Server 2016

## RD Gateway messaging isn't supported

Remote Desktop Client doesn't support RD Gateway messaging. Verify that the Remote Desktop Resource Access Policy (RD RAP) for your RD Gateway server doesn't specify **Only allow computers with support for RD Gateway Messaging**, or you aren't able to connect.