---
layout: Conceptual
title: What is System Insights? | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/system-insights/overview
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: manage
ms.update-cycle: 1095-days
description: Discover how System Insights uses predictive analytics in Windows Server to forecast and manage server resources.
ms.topic: overview
author: robinharwood
ms.author: roharwoo
ms.date: 2025-06-02T00:00:00.0000000Z
locale: en-us
document_id: 36246389-e0ce-8632-4393-7b08912e94e2
document_version_independent_id: 84388f36-9def-db80-39e4-d5430ea0823d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/system-insights/overview.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../administration/toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/system-insights/overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/system-insights/overview.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: a30f9435-0bf2-770a-f548-ab8f5c768a8c
---

# What is System Insights? | Microsoft Learn

System Insights brings predictive analytics to Windows Server, enabling you to forecast and manage server resources proactively. By analyzing local system data with machine learning models, System Insights helps you anticipate potential issues and optimize resource usage—reducing the need for reactive troubleshooting. This overview explains how System Insights works, its key features, and how you can use it to improve server management.

System Insights is available on Windows Server 2019 and newer. It runs on both host and guest machines, on any hypervisor, and in any cloud.

System Insights is preinstalled on Windows Server.

## Available capabilities

System Insights provides four capabilities that are enabled by default:

- CPU capacity forecasting - Forecasts CPU usage.
- Networking capacity forecasting - Forecasts network usage for each network adapter.
- Total storage consumption forecasting - Forecasts total storage consumption across all local drives.
- Volume consumption forecasting - Forecasts storage consumption for each volume.

[![Screenshot of System Insights extension and the available capabilities in Windows Admin Center.](media/system-insights-overview.png)](media/system-insights-overview.png#lightbox)

System Insights also has an [extensible infrastructure](adding-and-developing-capabilities), so Microsoft and third parties can add new predictive capabilities to System Insights without updating the operating system.

## Manage System Insights

You can manage System Insights through [Windows Admin Center](../windows-admin-center/overview), or [directly through PowerShell](/en-us/powershell/module/systeminsights/). Configure each predictive capability separately according to the needs of your deployment. All prediction results are published to the event log, so you can use [Azure Monitor](https://azure.microsoft.com/services/monitor/) or [System Center Operations Manager](/en-us/system-center/scom/welcome?view=sc-om-1807&amp;preserve-view=true) to easily aggregate and view predictions across a group of machines.

## Local functionality of System Insights

System Insights runs completely locally on Windows Server. All of your data is collected, persisted, and analyzed directly on your machine, so that you can realize predictive analytics capabilities without any cloud connectivity.

Your system data is stored on your machine, and this data is analyzed by predictive capabilities that don't require retraining in the cloud. With System Insights, you can retain your data on your machine and still benefit from predictive analytics capabilities.