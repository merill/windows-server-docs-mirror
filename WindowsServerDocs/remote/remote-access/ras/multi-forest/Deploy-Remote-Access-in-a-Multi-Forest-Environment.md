---
layout: Conceptual
title: Deploy Remote Access in a Multi-Forest Environment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/multi-forest/deploy-remote-access-in-a-multi-forest-environment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn about the planning and configuration steps for a multi-forest deployment; including when one-time password (OTP) authentication is used.
ms.topic: install-set-up-deploy
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 02ab59b9-1795-32aa-18cf-52162c333d1f
document_version_independent_id: 7903a636-5c9e-3fea-1083-97a0e0e46466
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/multi-forest/Deploy-Remote-Access-in-a-Multi-Forest-Environment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/multi-forest/deploy-remote-access-in-a-multi-forest-environment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/multi-forest/Deploy-Remote-Access-in-a-Multi-Forest-Environment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 04cce986-cb34-8cca-8bbb-436e849d79b1
---

# Deploy Remote Access in a Multi-Forest Environment | Microsoft Learn

The Remote Access configuration tools (the Remote Access Management console and the Windows PowerShell cmdlets) are designed to work well in a single forest environment containing one or more domains. However, when Remote Access is deployed in a multi-forest environment, the Remote Access administrator must perform some manual configuration for a successful deployment. This guide describes the planning and configuration steps for a multi-forest deployment; including when one-time password (OTP) authentication is used.

- [Plan a multiforest deployment](plan-a-multi-forest-deployment)
- [Configure a multiforest deployment](configure-a-multi-forest-deployment)