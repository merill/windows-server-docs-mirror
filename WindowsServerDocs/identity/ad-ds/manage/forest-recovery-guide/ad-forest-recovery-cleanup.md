---
layout: Conceptual
title: AD Forest Recovery - Cleanup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-cleanup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD Forest Recovery - Cleanup'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 5a291f65-794e-4fc3-996e-094c5845a383, inhenkel
locale: en-us
document_id: 7a24754c-0813-eabd-2c21-81909ab12059
document_version_independent_id: 7a24754c-0813-eabd-2c21-81909ab12059
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-cleanup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-cleanup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-cleanup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 354390ee-0f3b-d231-5f17-a7059ec8ecaf
---

# AD Forest Recovery - Cleanup | Microsoft Learn

Perform the following post recovery steps as needed:

## Revert to the original DNS configuration

After the entire forest is recovered, you can revert to the original DNS configuration, including configuration of the preferred and alternate DNS servers on each of the DCs. After the DNS servers are configured as they were before the malfunction, their previous name resolution capabilities will be restored. Delete any DNS records for DCs that haven't been recovered.

## Delete Windows Internet Name Service (WINS) records

Delete Windows Internet Name Service (WINS) records for all DCs that haven't been recovered.

## Transfer operations master roles to other DCs

You can transfer the operations master roles to other DCs in the domain or forest and add more global catalog servers based on the configuration before the failure.

## Recreate missing objects

Because the entire forest is restored to a previous state, any objects (such as users and computers) that were added and all updates (such as password changes) that were made to existing objects after this point are lost. Therefore, you should recreate these missing objects and reapply the missing updates as appropriate.

## Restore outgoing domains and trusts

You might also need to restore outgoing trusts with external domains and forests, because these external trust relationships aren't restored automatically from backups.