---
layout: Conceptual
title: Active Directory Forest Recovery Guide | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-guide
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: This guide contains recommendations for recovering an Active Directory forest if a forest-wide failure renders all DCs in the forest incapable of functioning normally.
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-09T00:00:00.0000000Z
ms.topic: troubleshooting
locale: en-us
document_id: 084b6f21-78fd-b0bb-18b4-96e3374f4e6e
document_version_independent_id: 084b6f21-78fd-b0bb-18b4-96e3374f4e6e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-guide.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-guide
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-guide.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: ed03ed47-5f47-ed0a-9f72-bf51239ec39a
---

# Active Directory Forest Recovery Guide | Microsoft Learn

This guide contains recommendations for recovering an Active Directory forest if a forest-wide failure renders all domain controllers (DCs) in the forest incapable of functioning normally. The steps it contains serve as a template for your forest recovery plan, which you can customize for your environment. These steps apply to DCs that run Microsoft Windows Server 2022, 2019, 2016, 2012 R2, and 2012 operating systems.

## Steps outlined in this guide

- [AD Forest Recovery - Prerequisites](ad-forest-recovery-prerequisites)
- [AD Forest Recovery - Devise a custom forest recovery plan](ad-forest-recovery-devise-a-plan)
- [AD Forest Recovery - Steps to restore the forest](ad-forest-recovery-steps-for-restoring-the-forest)
- [AD Forest Recovery - Identify the problem](ad-forest-recovery-identify-the-problem)
- [AD Forest Recovery - Determine how to recover](ad-forest-recovery-determine-how-to-recover)
- [AD Forest Recovery - Perform initial recovery](ad-forest-recovery-perform-initial-recovery)
- [AD Forest Recovery - Procedures](ad-forest-recovery-procedures)
- [AD Forest Recovery - Frequently Asked Questions (FAQ)](ad-forest-recovery-faq)
- [AD Forest Recovery - Recover a single domain within a multidomain forest](ad-forest-recovery-recover-single-domain-multidomain-forest)
- [AD Forest Recovery - Redeploy remaining DCs](ad-forest-recovery-restore-additional-dcs)
- [AD Forest Recovery - Virtualization](ad-forest-recovery-virtualization)
- [AD Forest Recovery - Cleanup](ad-forest-recovery-cleanup)

## Legacy guidance

You can find guidance for older operating systems in the [Windows Server archive](/en-us/previous-versions/windows/).