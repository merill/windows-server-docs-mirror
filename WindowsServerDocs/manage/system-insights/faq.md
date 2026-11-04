---
layout: Conceptual
title: System Insights FAQ | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/system-insights/faq
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: manage
ms.update-cycle: 1095-days
description: System Insights FAQ
ms.topic: faq
author: robinharwood
ms.author: roharwoo
ms.date: 2025-06-09T00:00:00.0000000Z
locale: en-us
document_id: 91655a60-442e-01a9-0f2a-567d7408bdb2
document_version_independent_id: 2c686535-0be2-0aed-6a82-7e2c2a72f2f8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/system-insights/faq.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../administration/toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/system-insights/faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/system-insights/faq.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/2bb407c5-c939-4f7a-9174-27da19279675
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/6eda2a8b-e231-4335-b766-c055ea6025a6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 17fc486a-eeac-b7ac-1695-7936c9ae06d6
---

# System Insights FAQ | Microsoft Learn

## How can you use System Insights with Azure Monitor or System Center Operations Manager?

[Azure Monitor](https://azure.microsoft.com/services/monitor/) and [System Center Operations Manager](/en-us/system-center/scom/welcome?view=sc-om-1807&amp;preserve-view=true) provide operational information across your deployments to help you manage your infrastructure. System Insights, in contrast, is a Windows Server feature that introduces local predictive analytics capabilities. Together, System Insights and Azure Monitor or SCOM can help surface the predictions across a population of devices:

Azure Monitor or SCOM can key off the events created by System Insights, as System Insights outputs the result of each prediction to the event log. They can surface these machine-specific predictions across a fleet of Windows Servers, enabling you to have a unified view of these predictions across a group of server instances.

See the channel and event IDs for each prediction in [retrieve capability results](managing-capabilities#retrieve-capability-results).

## How does System Insights relate to Windows ML?

[Windows ML](/en-us/windows/uwp/machine-learning/) is a platform that enables developers to import and score pre-trained machine learning models on Windows devices. These models benefit from hardware acceleration, and they can be scored locally.

System Insights is a feature in Windows Server 2019 that offers local predictive capabilities together with a complete management experience, including PowerShell and Windows Admin Center integration.

## Can I use System Insights for my cluster?

Yes. System Insights can independently run on each individual failover cluster node, and the default behavior of System Insights forecasts usage across local storage, volume, CPU, and networking. **You can also enable forecasting for clustered storage**, so the storage forecasting capabilities predict usage for clustered volumes and storage. You can manage these settings in Windows Admin Center or PowerShell.

## How expensive is it to run the default capabilities?

Each default capability is inexpensive to run. Each capability takes longer to run as you collect more data, but they typically should complete in a few seconds.