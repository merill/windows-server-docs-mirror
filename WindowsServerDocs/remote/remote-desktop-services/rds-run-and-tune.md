---
layout: Conceptual
title: RDS - Run and tune your Remote Desktop Services environment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-run-and-tune
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Provides management information for Remote Desktop Services.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: best-practice
author: robinharwood
locale: en-us
document_id: c01c1283-311b-8292-9efb-b485c928542e
document_version_independent_id: bef89ccd-43f1-1cf4-0b09-bcb9743194e6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-run-and-tune.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-run-and-tune
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-run-and-tune.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 3097e8ef-0712-b80b-f62b-355bc62f10b6
---

# RDS - Run and tune your Remote Desktop Services environment | Microsoft Learn

Tuning your deployment takes time and requires instrumentation and monitoring. Use the processes below to refine your Remote Desktop deployment, keep it running and enable scaling out (and in) as needed.

It's a good practice to continually assess the metrics and balance against running costs.

## Management and monitoring

Check out [Manage users in your RDS collection](rds-user-management) for information about how to manage access to your desktops and remote resources.

Use **Microsoft Operations Management Suite (OMS)** to monitor Remote Desktop deployments for potential bottlenecks and manage them using one of the following ways:

- **Server Manager**: Use the RD management tool that is built in to Windows Server to manage deployments with up to 500 concurrent remote end-users.
- **PowerShell**: Use the RD PowerShell module, also built into Windows Server, to manage deployments with up to 5000 concurrent remote end-users.

## Scale: Bigger, better, faster

With visibility into the deployment, you can control scale with more precision. Easily add or remove Remote Desktop host servers based on scale needs.

Remote Desktop deployments that are built on Azure can make use of Azure services, like Azure SQL, to scale automatically on demand.

## Automation: Script for success

Maintaining a running, highly scaled application involves repeating operations on a regular basis. Use Remote Desktop Services PowerShell cmdlets and WMI providers to develop scripts that can be run on multiple deployments when needed. Run Best Practice Analyzer (BPA) rules for Remote Desktop Services on your deployments to tune your deployments.

## Load testing: Avoid surprises

Load test the deployment with both stress tests and simulation of real-life usage. Vary the load size to avoid surprises! Ensure that responsiveness meets user requirements, and that the entire system is resilient. Create load tests with simulation tools, like LoginVSI, that check your deployment's ability to meet the users' needs.