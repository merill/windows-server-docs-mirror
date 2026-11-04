---
layout: Conceptual
title: Choosing a BranchCache Design | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/branchcache/plan/choosing-a-branchcache-design
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to learn about BranchCache modes and to select the best modes for your deployment.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-05T00:00:00.0000000Z
locale: en-us
document_id: dfc4e34c-6c6e-093d-2af9-af41d7edfb43
document_version_independent_id: 6a7a3dc7-6dcb-4084-ab65-df7e3d30cdd7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/branchcache/plan/Choosing-a-BranchCache-Design.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/branchcache/plan/choosing-a-branchcache-design
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/branchcache/plan/Choosing-a-BranchCache-Design.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: d0a5939e-bad4-37bf-abea-94bddb0fa44d
---

# Choosing a BranchCache Design | Microsoft Learn

You can use this topic to learn about BranchCache modes and to select the best modes for your deployment.

You can use this guide to deploy BranchCache in the following modes and mode combinations.

- All branch offices are configured for distributed cache mode.
- All branch offices are configured for hosted cache mode and have a hosted cache server on site.
- Some branch offices are configured for distributed cache mode and some branch offices have a hosted cache server on site and are configured for hosted cache mode.

The following illustration depicts a dual mode installation, with one branch office configured for distributed cache mode and one branch office configured for hosted cache mode.

![Choosing a BranchCache design](../../media/choosing-a-branchcache-design/bc_new_modes.jpg)

Before you deploy BranchCache, select the mode you prefer for each branch office in your organization.