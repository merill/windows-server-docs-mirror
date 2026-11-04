---
layout: Conceptual
title: AD Forest Recovery - Devising an AD Forest Recovery Plan | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-devise-a-plan
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD Forest Recovery - Devising an AD Forest Recovery Plan'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 17381f30-55f2-4e00-977a-b701675fa4ff, inhenkel
locale: en-us
document_id: adb0045a-be6a-9bb9-da22-56972747dbe4
document_version_independent_id: adb0045a-be6a-9bb9-da22-56972747dbe4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-devise-a-plan.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-devise-a-plan
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-devise-a-plan.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 2400c238-9fbe-f961-aa92-804d9e65c13d
---

# AD Forest Recovery - Devising an AD Forest Recovery Plan | Microsoft Learn

Depending on your environment and business requirements, you may not need to perform all the steps described in this guide to perform a successful forest recovery. Given that this guide serves only as a template for forest recovery, it's vital that you devise a custom forest recovery plan that suits your environment and meets your business needs.

## Plan

For example, in your forest recovery plan, you should have a detailed topology map of your forests. The map should list all the information about the DCs, such as their names, their roles and back up status, and the trust relationships between them.

## Practice

You should practice your forest recovery plan at least once a year. Also, it's a good idea to perform a forest recovery drill when there are membership changes to the Enterprise Admins or Domain Admins group. This helps ensure that your information technology (IT) staff fully understands the forest recovery plan.