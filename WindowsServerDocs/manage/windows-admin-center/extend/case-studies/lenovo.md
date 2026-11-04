---
layout: Conceptual
title: Windows Admin Center SDK Case Study - Lenovo | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/case-studies/lenovo
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Windows Admin Center SDK Case Study - Lenovo
ms.topic: partner-tools
author: robinharwood
ms.author: roharwoo
ms.date: 2019-01-07T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: cda180be-8522-9606-d465-5f656319a8a0
document_version_independent_id: b6e2aa78-a0c9-d57c-7b6f-e213c5460866
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/case-studies/lenovo.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/case-studies/lenovo
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/case-studies/lenovo.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 9fa9cbb1-f327-d40f-8b22-c4f127a55afa
---

# Windows Admin Center SDK Case Study - Lenovo | Microsoft Learn

## Integrated hardware management everywhere!

The [Lenovo XClarity Integrator](https://www.lenovo.com/us/en/data-center/software/systems-management/XClarity-Integrator/p/WMD00000370) extension for Windows Admin Center provides administrators a seamless experience to manage Lenovo infrastructure directly from Windows Admin Center. The XClarity Integrator extension includes a standalone solution extension and also extends the existing Server Manager, Failover Cluster Manager, and Hyper-Converged Cluster Manager solutions in a single, unified UI to enable simple server management.

The solution extension included in the XClarity Integrator extension allows connecting to a Lenovo XClarity Administrator, Lenovo rack or tower servers, or all the servers in an entire chassis at once. Once the servers are added, you can see the overall health status for all added nodes.

![Screenshot of the Lenovo XClarity Integrator extension in Windows Admin Center showing the overall health status for all added nodes.](../../media/extend-case-study-lenovo/lenovo-1.png)

By selecting a server, you can view the server's hardware inventory, available firmware updates, alerts, events, logs, power consumption and temperature. You can also run operations such as Remote Control and power on/off.

![Screenshot of the Lenovo XClarity Integrator extension in Windows Admin Center showing the Inventory page.](../../media/extend-case-study-lenovo/lenovo-2.png)

The same tools are available as a tool extension when managing servers within Windows Admin Center as well, allowing you to seamlessly switch between managing your infrastructure software and hardware.

![Screenshot of the Server Manager portal in Windows Admin Center showing the Lenovo XClarity Integrator extension tool.](../../media/extend-case-study-lenovo/lenovo-3.png)

The tool extension for failover clusters and hyper-converged clusters provides a dashboard displaying overall cluster hardware health status, status alerts, firmware consistency status and report, power consumption and temperature, and fan and power supply health status.

![Screenshot of the Lenovo XClarity Integrator extension tool showing the Dashboard page.](../../media/extend-case-study-lenovo/lenovo-4.png)![Screenshot of the Lenovo XClarity Integrator extension tool showing the Firmware Consistency Report page.](../../media/extend-case-study-lenovo/lenovo-5.png)

The solution extension and tool extensions for Windows servers and clusters provide the rolling (cluster-aware) server update functions. This can help prevent any workload interruption during server updates. Currently, the extensions support individual firmware updates and compliance policy firmware updates for any Lenovo servers. They also support best recipe firmware/driver updates for Lenovo ThinkAgile MX HCI cluster servers.

![Screenshot of the Lenovo XClarity Integrator extension tool showing the System Updates Method Selection page.](../../media/extend-case-study-lenovo/lenovo-6-fwupdate.png)

The tool extension for hyperconverged clusters provides the disk/storage pool management functions for Lenovo ThinkAgile MX HCI cluster servers. These functions include the server rear/front graphic view to present server and disk status. With the help of both the wizard and graphic view, operations like adding a disk to the storage pool, removing a disk from the storage pool, replacing a disk, or locating a server/disk by lighting on the server/disk location LEDs become much easier.

![Screenshot of the Lenovo XClarity Integrator extension tool showing the Disk Manager page.](../../media/extend-case-study-lenovo/lenovo-7-diskmgr.png)

In version 2.1, Lenovo extensions introduced role-based access control capabilities. These capabilities are enabled if Lenovo XClarity Administrator is applied for hardware management.

Learn more about the Lenovo XClarity Integrator offerings for Windows Admin Center on the [Lenovo website](https://support.lenovo.com/us/en/solutions/ht507549).