---
layout: Conceptual
title: Import Data Packages on the Hosted Cache Server (Optional) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/bc-hcm/9-bc-import-data
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to import data packages and preload content on your hosted cache servers.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 18e4aec1-4d60-ac96-99a9-9c56fe212169
document_version_independent_id: 9028c74e-af5b-0242-8f7d-08232293f710
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/9-Bc-Import-Data.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/bc-hcm/9-bc-import-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/bc-hcm/9-Bc-Import-Data.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 8a264815-811e-aab0-a687-4e58ea5c33a9
---

# Import Data Packages on the Hosted Cache Server (Optional) | Microsoft Learn

You can use this procedure to import data packages and preload content on your hosted cache servers.

This procedure is optional because you are not required to prehash and preload content on your hosted cache servers.

If you do not pre-load content, data is added to the hosted cache automatically as clients download it over the WAN connection.

You must be a member of the Administrators group to perform this procedure.

## To import data packages on the hosted cache server

1. On the server computer, open Windows PowerShell with Administrator privileges.
2. Type the following command, replacing the value for the –Path parameter with the folder location where you have stored your data packages, and then press ENTER.

    ```
    Import-BCCachePackage –Path D:\temp\PeerDistPackage.zip
    ```
3. If you have more than one hosted cache server where you want to preload content, perform this procedure on each hosted cache server.

To continue with this guide, see [Configure Client Automatic Hosted Cache Discovery by Service Connection Point](10-bc-client-by-scp).