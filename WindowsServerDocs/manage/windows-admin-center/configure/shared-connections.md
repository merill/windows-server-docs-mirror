---
layout: Conceptual
title: Configure shared connections for all users of the Windows Admin Center gateway | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/configure/shared-connections
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn how administrators can configure their Windows Admin Center (Project Honolulu) gateway once to let all users share a single list of connections.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2021-10-18T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 7a587c51-9a47-0528-aacb-b00c9402f813
document_version_independent_id: f3eb8169-3d20-c6e9-851f-1421a2d7f85c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/configure/shared-connections.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/configure/shared-connections
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/configure/shared-connections.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: b8e849ea-2d03-b4bf-ce5f-cbff4c88c443
---

# Configure shared connections for all users of the Windows Admin Center gateway | Microsoft Learn

Shared connections in Windows Admin Center are gateway-managed server, cluster, and PC connections that appear for every user of a gateway. Gateway administrators can maintain one consistent list instead of requiring each user to add the same connections and tags individually. Shared connections are available only in Administration Mode, not Virtualization Mode.

This article explains where gateway administrators add shared connections and tags, and how Windows Admin Center shows shared and personal connections to gateway users.

Gateway administrators can add servers, clusters, and PC connections, and assign tags, on the **Shared Connections** tab in the Windows Admin Center gateway settings. The connections and tags appear on the **All Connections** page for all users of the gateway.

![Screenshot of the Windows Admin Center Shared Connections page showing six servers tagged redmond.](../media/shared-cnxns-1.png)

When any Windows Admin Center user accesses the "All Connections" page after Shared Connections have been configured, they will see their connections grouped into two sections: Personal and Shared connections. The Personal group is a specific user's connection list and persists across that user's browser sessions. The Shared connections group is the same across all users, and cannot be modified from the All Connections page.

![Screenshot of the Windows Admin Center All Connections page showing Personal and Shared connection groups.](../media/shared-cnxns-2.png)