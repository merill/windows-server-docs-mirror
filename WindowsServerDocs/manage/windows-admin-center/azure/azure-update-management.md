---
layout: Conceptual
title: Use Windows Admin Center to manage operating system updates with Azure Update Management | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/azure/azure-update-management
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Use Windows Admin Center (Project Honolulu) to set up Azure Update Management to manage OS updates.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2021-10-18T00:00:00.0000000Z
locale: en-us
document_id: 7ddde58c-b128-33ab-6c1d-dec6c4590455
document_version_independent_id: f7816f53-51bd-a908-5097-15c6e65f6e27
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/azure/azure-update-management.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/azure/azure-update-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/azure/azure-update-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5fecc40f-ea4d-f02d-79c9-22b25ebb6899
---

# Use Windows Admin Center to manage operating system updates with Azure Update Management | Microsoft Learn

[Learn more about Azure integration with Windows Admin Center.](./)

Azure Update Management is a solution in Azure Automation that allows you to manage updates and patches for multiple machines from a single place, rather than on a per-server basis. With Azure Update Management, you can quickly assess the status of available updates, schedule installation of required updates, and review deployment results to verify updates that apply successfully. This is possible whether your machines are Azure virtual machines (VMs), hosted by other cloud providers, or on premises. [Learn more about Azure Update Management](/en-us/azure/automation/update-management/overview).

With Windows Admin Center, you can easily set up and use Azure Update Management to keep your managed servers up to date. If you don't already have a Log Analytics workspace in your Azure subscription, Windows Admin Center will automatically configure your server and create the necessary Azure resources in the subscription and location you specify. If you have an existing Log Analytics workspace, Windows Admin Center can automatically configure your server to consume updates from Azure Update Management.

To get started, go to the Updates tool in a server connection and select “Set up now”, and provide your preferences for the related Azure resources.

Once you've configured your server to be managed by Azure Update Management, you can access Azure Update Management by using the hyperlink provided in the Updates tool.

[Learn how to stop using Azure Update Management to update your server.](azure-monitor#disabling-monitoring)

Note that you must [register your Windows Admin Center gateway with Azure](azure-integration) before setting up Azure Update Management.