---
layout: Conceptual
title: Windows Admin Center SDK Case Study - Fujitsu | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/extend/case-studies/fujitsu
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Windows Admin Center SDK Case Study - Fujitsu
ms.topic: partner-tools
author: robinharwood
ms.author: roharwoo
ms.date: 2018-05-23T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 0eeecce8-3580-9024-4714-7dddba36e9b6
document_version_independent_id: d06ab068-718c-0ba8-9e34-7dbc4af29a98
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/extend/case-studies/fujitsu.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/extend/case-studies/fujitsu
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/extend/case-studies/fujitsu.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: f98d9fd6-3d0b-0eb0-1bf4-65ac5579b834
---

# Windows Admin Center SDK Case Study - Fujitsu | Microsoft Learn

## Bringing end-to-end visibility, from operating system to hardware, into Windows Admin Center

Fujitsu is a leading Japanese information and communication technology company and a manufacturer of [PRIMERGY](http://www.fujitsu.com/fts/products/computing/servers/primergy/) and [PRIMEQUEST](http://www.fujitsu.com/fts/products/computing/servers/mission-critical/) server products. The [Fujitsu ServerView management suite](http://www.fujitsu.com/fts/products/computing/servers/primergy/management/) provides a comprehensive toolset for server lifecycle management including a server-side agent that provides a CIM and PowerShell interface for hardware management.

Fujitsu saw an opportunity to easily integrate with Windows Admin Center as it provided CIM and PowerShell interfaces that could communicate with the server-side agents. The development team at Fujitsu was able to easily implement the CIM calls they were familiar with to the agent and visualize the information within Windows Admin Center using the available UI components.

![Fujitsu extension - Health tree view](../../media/extend-case-study-fujitsu/health-tree.png)

Once the team became familiar with the Windows Admin Center SDK, adding UI to expose additional hardware information was often simply a few more lines of HTML code and they were quickly able to expand from a single tool to displaying a summary view of hardware component health, detailed views for system event logs, driver monitor, separate views for processor, memory, fans, power supplies, temperatures and voltages, and even an additional tool for RAID management. Using UI controls available in the SDK such as the tree, grid and detail pane controls enabled the team to quickly build UI and also achieve a visual and interaction design very similar to the rest of Windows Admin Center.

![Fujitsu extension - RAID tree view](../../media/extend-case-study-fujitsu/raid-tree.png)

![Fujitsu extension - RAID volumes view](../../media/extend-case-study-fujitsu/raid-volumes.png)

The partnership between Fujitsu and the Windows Admin Center team clearly shows the value of integration within Windows Admin Center, enabling customers to have end-to-end insight into server roles and services, to the operating system, and to hardware management.