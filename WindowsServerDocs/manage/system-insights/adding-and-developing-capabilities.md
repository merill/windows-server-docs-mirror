---
layout: Conceptual
title: Add and develop capabilities in System Insights | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/system-insights/adding-and-developing-capabilities
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: manage
ms.update-cycle: 1095-days
description: System Insights enables you to add new predictive capabilities to System Insights, without requiring any OS updates. This enables developers, including Microsoft and third parties, to create and deliver new capabilities mid-release to address the scenarios you care about. New capabilities can specify custom data to collect and analyze, and they also integrate with the existing System Insights management planes.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2025-06-06T00:00:00.0000000Z
locale: en-us
document_id: 519a0668-fef9-674c-7f48-165ee9c9cbfc
document_version_independent_id: 3c30e45f-1416-87d9-cf60-c445987a54aa
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/system-insights/adding-and-developing-capabilities.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../administration/toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/system-insights/adding-and-developing-capabilities
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/system-insights/adding-and-developing-capabilities.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 7b4fb090-023c-661b-c3e6-1af46d8f2ff5
---

# Add and develop capabilities in System Insights | Microsoft Learn

System Insights enables you to add new predictive capabilities to System Insights, without requiring any OS updates. This enables developers, including Microsoft and third parties, to create and deliver new capabilities mid-release to address the scenarios you care about.

Any new capability can integrate with and extend the existing System Insights infrastructure:

- New capabilities can **specify any performance counter or system event**, which are collected, persisted locally, and returned to the capability for analysis when the capability is invoked.
- New capabilities can **use the existing Windows Admin Center and PowerShell management planes**. Not only are new capabilities be discoverable in System Insights, they also benefit from custom schedules and remediation actions.

## Manage new capabilities

- [Learn](add-remove-update-capabilities) how to add, remove, and update capabilities using PowerShell.

## Develop a capability

Use the following resources to help you get started writing your own custom capabilities:

- [Learn](data-sources) about the data sources you can collect.
- [Download](https://www.nuget.org/packages/Microsoft.WindowsServer.SystemInsights/) the System Insights NuGet package, which contains the classes and interfaces you need to write a capability.
- [Read](/en-us/dotnet/api/microsoft.systeminsights.capability) the API documentation to learn about the System Insights classes and interfaces.
- [Use](https://aka.ms/systeminsights-samplecapability) the System Insights sample capability to help you get started. This shows you how to register a capability, specify the data sources to collect, and start analyzing system data.