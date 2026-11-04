---
layout: Conceptual
title: Windows Admin Center SDK Case Study - QCT | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/case-studies/qct
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Windows Admin Center SDK Case Study - QCT
ms.topic: partner-tools
author: robinharwood
ms.author: roharwoo
ms.date: 2019-06-14T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: a12a258f-d88e-a85c-fecb-d7f9e647ad46
document_version_independent_id: edc110ac-508e-5def-ea4f-9202b0d5891c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/case-studies/qct.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/case-studies/qct
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/case-studies/qct.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 6c4d7f94-a1d0-8ad7-16ee-acf2820838ec
---

# Windows Admin Center SDK Case Study - QCT | Microsoft Learn

## A simple path to server infrastructure management

The QCT Management Suite extension for Windows Admin Center provides a single pane of glass dashboard for monitoring system configurations and managing server health of [QCT Azure Local certified systems](https://go.qct.io/solutions/enterprise-private-cloud/qxstack-azure-stack-hci-solution/) : [QuantaGrid D52BQ-2U](https://www.qct.io/product/index/Server/rackmount-server/2U-Rackmount-Server/QuantaGrid-D52BQ-2U), [QuantaGrid D52T-1ULH](https://www.qct.io/product/index/Storage/Storage-Server/1U-Storage-Server/QuantaGrid-D52T-1ULH) and [QuantaPlex T21P-4U](https://www.qct.io/product/index/Storage/Storage-Server/4U-Storage-Server).

Driven by customer pain points around existing monitoring and management, QCT provides exclusive, complementary features and functions, which includes an overview of system event logs, monitoring drivers, and hardware component health to enhance the overall management experience.

![Screenshot of the Disk tab of the QCT extension.](../../media/extend-case-study-qct/d52t_darkmode_disk-detail-general.png)

The QCT Management Suite extends the functionality of Windows Admin Center with the key features below:

- **One-click exclusive hardware management** - An intuitive user interface displays hardware information, including model name, processor, memory and BIOS. IT administrators can restart the BMC with a simple one-click UI.

![Screenshot of the One-click exclusive hardware management feature of the QCT extension.](../../media/extend-case-study-qct/d52t_overview.png)

- **Disk mapping and LED identification for efficient service support** - QCT Management Suite wizard UI design displays the slot of each selected disk with an overview of disk profiles and LED light controls of selected disks for efficient replacement.

![Screenshot of the Disk Replacement feature of the QCT extension.](../../media/extend-case-study-qct/t21p_disk_mapping.png)

- Easy-to-use monitoring tool for hardware event log and health status.

![Screenshot of the monitoring tool for hardware event log and health status that is included in the QCT extension.](../../media/extend-case-study-qct/d52t_event_log.png)

- **Predictive disk management** - Evaluate the system condition with S.M.A.R.T information and unhealthy notifications which allow organizations to take action before total failure occurs.

![Screenshot of the S.M.A.R.T information and unhealthy notifications that are included in the QCT extension.](../../media/extend-case-study-qct/t21p_smart.png)

Learn more about the QCT Management Suite for Windows Admin Center:

- [QCT Management Suite (Windows Admin Center Extension)](https://go.qct.io/solutions/enterprise-private-cloud/qxstack-windows-2019-server-solution/)
- [QCT Management Suite datasheet](https://go.qct.io/wp-content/uploads/2019/04/WAC-data-sheet_v04222019.pdf)