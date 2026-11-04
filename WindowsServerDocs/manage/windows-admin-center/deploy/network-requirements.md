---
layout: Conceptual
title: Windows Admin Center Network Requirements | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/deploy/network-requirements
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Networking requirements to use Windows Admin Center.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2023-01-12T00:00:00.0000000Z
locale: en-us
document_id: d81cd846-91e6-dc59-57cc-c0a25ffe9a92
document_version_independent_id: d81cd846-91e6-dc59-57cc-c0a25ffe9a92
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/deploy/network-requirements.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/deploy/network-requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/deploy/network-requirements.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: b28597c2-35ff-a66b-839e-2e5a567b3996
---

# Windows Admin Center Network Requirements | Microsoft Learn

This article describes the networking requirements for using Windows Admin Center to manage your servers and clusters.

## Networking configuration

Windows Admin Center communicates outbound securely to endpoints over TCP port 443. By default, the Windows Admin Center gateway and browser use the default route to the internet to perform actions. You can optionally configure the gateway to use a proxy server if your network requires it.

You need to open endpoints on two sources:

- **Gateway**: This server or client machine is where you install the Windows Admin Center gateway (.exe).
- **Browser**: This machine is where you access the Windows Admin Center web service.

If your firewall or proxy server restricts outbound connectivity, make sure that it doesn't block the URLs listed in the following section.

## Gateway URLs

| URL | Description | When required |
| --- | --- | --- |
| `aka.ms` | Acquire and maintain Windows Admin Center | Always. |
| `download.microsoft.com` | Acquire and maintain Windows Admin Center | Always. |
| `pkgs.dev.azure.com` | Extension management | Always. |
| `*.vsblob.visualstudio.com` | Extension management | Always. |
| `login.microsoftonline.com` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure public cloud. |
| `graph.microsoft.com` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure public cloud. |
| `graph.windows.net` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure public cloud. |
| `management.azure.com` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure public cloud. |
| `login.microsoftonline.us` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure US Government cloud. |
| `management.usgovcloudapi.net` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure US Government cloud. |
| `graph.windows.net` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure US Government cloud. |
| `management.core.usgovcloudapi.net` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure US Government cloud. |
| `login.partner.microsoftonline.cn` | Azure endpoints for communication | When you use Azure Hybrid Services in Azure operated by 21Vianet. |
| `management.chinacloudapi.cn` | Azure endpoints for communication | When you use Azure Hybrid Services in Azure operated by 21Vianet. |
| `graph.chinacloudapi.cn` | Azure endpoints for communication | When you use Azure Hybrid Services in Azure operated by 21Vianet. |
| `management.core.chinacloudapi.cn` | Azure endpoints for communication | When you use Azure Hybrid Services in Azure operated by 21Vianet. |

### Browser URLs

| URL | Description | When required |
| --- | --- | --- |
| `winadmincenterassets.blob.core.windows.net` | Extension management | Always. |
| `js.monitor.azure.com` | Extension management | Always. |
| `nuget.org` | Extension management | Always. |
| `announcements.blob.core.windows.net` | Extension management | Always. |
| `browser.events.data.microsoft.com` | Acquire and maintain Windows Admin Center | Optionally. |
| `login.microsoftonline.com` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure public cloud. |
| `graph.microsoft.com` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure public cloud. |
| `graph.windows.net` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure public cloud. |
| `portal.azure.com` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure public cloud. |
| `login.microsoftonline.us` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure US Government cloud. |
| `management.usgovcloudapi.net` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure US Government cloud. |
| `graph.windows.net` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure US Government cloud. |
| `portal.azure.us` | Azure endpoints for communication | When you use Azure Hybrid Services in the Azure US Government cloud. |
| `login.partner.microsoftonline.cn` | Azure endpoints for communication | When you use Azure Hybrid Services in Azure operated by 21Vianet. |
| `management.chinacloudapi.cn` | Azure endpoints for communication | When you use Azure Hybrid Services in Azure operated by 21Vianet. |
| `graph.chinacloudapi.cn` | Azure endpoints for communication | When you use Azure Hybrid Services in Azure operated by 21Vianet. |
| `portal.azure.cn` | Azure endpoints for communication | When you use Azure Hybrid Services in Azure operated by 21Vianet. |