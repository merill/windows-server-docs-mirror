---
layout: Conceptual
title: Windows Admin Center SDK Case Study - NEC | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/case-studies/nec
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Windows Admin Center SDK Case Study - NEC
ms.topic: partner-tools
author: robinharwood
ms.author: roharwoo
ms.date: 2019-04-01T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: e9f4bcde-2217-eaf2-f642-dae8e58f5aa1
document_version_independent_id: 3a3cfafb-3c5c-337a-c650-65a6cd4df3bd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/case-studies/nec.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/case-studies/nec
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/case-studies/nec.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 0a6ec594-e2ac-c493-e9b8-f9055ad81c28
---

# Windows Admin Center SDK Case Study - NEC | Microsoft Learn

NEC provides products for businesses, ranging from terminals to network and computer equipment, software products and service platforms, as well as integrated platforms based on these products and services.

NEC ESMPRO is NEC's server management software to manage NEC Express5800 series servers, and the NEC ESMPRO extension for Windows Admin Center enables showing hardware and RAID information of NEC Express5800 series servers in Windows Admin Center.

The NEC ESMPRO extension requires installing the NEC ESMPRO Manager as it retrieves server hardware information through the NEC ESMPRO Manager.

![Screenshot of the NEC ESMPRO extension in Windows Admin Center showing the System Overview page.](../../media/extend-case-study-nec/nec-1.png)

The NEC ESMPRO extension has two tabs, the 'System Overview' tab and the 'System Health' tab. In the System Overview tab, you can easily view the system's basic information.

![Screenshot of the NEC ESMPRO extension in Windows Admin Center showing the System Health page.](../../media/extend-case-study-nec/nec-2.png)

In the System Health tab, you can view the detailed information of individual hardware components, such as processors, memory, power supplies, network adapters, temperature and fan. The status and configuration for RAID systems, power consumption and hardware event logs are also available.

The NEC ESMPRO extension for Windows Admin Center brings new experiences of server management to server administrators with the collaboration of NEC's hardware technology and Microsoft's software technology.