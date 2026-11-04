---
layout: Conceptual
title: Windows Admin Center SDK Case Study - Thomas-Krenn | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/case-studies/thomas-krenn
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Windows Admin Center SDK Case Study - Thomas-Krenn
ms.topic: partner-tools
ms.author: roharwoo
author: robinharwood
ms.date: 2019-06-24T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 4328cac4-71fa-83e8-31af-f652493cf435
document_version_independent_id: bae2ed20-aa8d-b645-d1fd-f1f5069c94d5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/case-studies/thomas-krenn.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/case-studies/thomas-krenn
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/case-studies/thomas-krenn.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b41c4eb4-88d4-e18b-b1c3-8c1cdc7970e7
---

# Windows Admin Center SDK Case Study - Thomas-Krenn | Microsoft Learn

## Intuitive server and storage health management

The Thomas Krenn.AG Windows Admin Center extension is designed specifically for the highly available, 2-node [S2D Micro-Cluster](https://www.thomas-krenn.com/en/products/application/software-defined-storage/microsoft-s2d-azure-local/azure-stack-hci-microcluster.html) appliance. The user-friendly, graphical web interface visualizes a Micro-Cluster's health status through a simple dashboard and allows you to drill down on storage devices, network interfaces or the entire cluster to view more details.

The extension provides intuitive access to information typically needed for first-level service and support calls, such as serial numbers, software versions, storage utilization and more. It is designed to be useful to admins who have no prior experience with Windows Server hyper-converged infrastructure.

A few of the insights available are:

- General Information about the Micro-Nodes and the Micro-Cluster
- OS / boot device status
- Capacity HDD and caching SSD status
- Cluster events
- Network status and information

Use the dashboard to determine the cluster's health status and important system information such as serial numbers, model, OS version and utilization. Additionally, fan, NIC and overall node hardware health are displayed on the dashboard as well.

![Screenshot of the Thomas-Krenn extension showing the cluster's health status and important system information.](../../media/extend-case-study-thomas-krenn/thomas-krenn-1.png)

You can drill down into storage devices to view serial numbers, SMART-status, and capacity utilization. Boot devices also show wear out indicators, reallocated sectors and power on time, which are the best indicators of SSD health.

![Screenshot of the Thomas-Krenn extension showing serial numbers, SMART-status, and capacity utilization of the storage devices.](../../media/extend-case-study-thomas-krenn/thomas-krenn-2.png)

The cluster status icon expands to show a summary of the cluster's operational details.

![Screenshot of the Thomas-Krenn extension showing the cluster's operational details](../../media/extend-case-study-thomas-krenn/thomas-krenn-3.png)

After this Micro-Cluster's Azure cloud witness was unavailable for a whole night, one glance is enough to identify the problem. Clicking on “Notifications” immediately lists relevant events for quick remediation. Cluster events are localized and determined by the base OS language. The extension itself supports English and German.

![Screenshot of the Thomas-Krenn extension showing the Notifications tab of the Cluster Details.](../../media/extend-case-study-thomas-krenn/thomas-krenn-4.png)

Network information is readily available as well.

![Screenshot of the Thomas-Krenn extension showing the network information that is readily available. ](../../media/extend-case-study-thomas-krenn/thomas-krenn-5.png)

Based on customer feedback, we've also implemented “Dark Mode” available in Windows Admin Center v1904. This is soothing in dark datacenters and in poorly lighted cabinets and closets. It also makes Windows Admin Center more accessible by reducing glare for admins with certain visual impairments.

![Screenshot of the Thomas-Krenn extension showing Dark Mode available in Windows Admin Center v1904.](../../media/extend-case-study-thomas-krenn/thomas-krenn-6.png)

Thomas-Krenn immediately realized that usability and accessibility for untrained admins would be key to a great customer experience for hyper-converged infrastructure in the small and mid-sized business market. Thomas-Krenn's Micro-Cluster extension perfectly complements Windows Admin Center's native HCI management capabilities by including proprietary hardware information on the dashboard and re-grouping important cluster health information in a new, human-friendly interface.

During the development process it was decided to deploy Windows Admin Center 1904 in a high-availability configuration on the cluster itself, ensuring manageability even after node failures. The extension comes pre-installed, just as the entire OS.

The extension was built in parallel with Windows Admin Center 1904 being developed at Microsoft. Close cooperation and continuous feedback exposed issues on both sides that were jointly resolved before the product successfully launched in April 2019. Thomas-Krenn is incredibly proud to be one of the first to fully support and implement Windows Admin Center 1904's new features.