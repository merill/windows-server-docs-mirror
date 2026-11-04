---
layout: Conceptual
title: AD Forest Recovery - Steps for Restoring the forest | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-steps-for-restoring-the-forest
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: This section provides an overview of the recommended path for recovering a forest. The forest recovery steps are described in detail later.
ms.author: roharwoo
author: robinharwood
ms.date: 2023-06-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: b1c76b4a-bdec-2939-8845-c9a1fdb82cfc
document_version_independent_id: b1c76b4a-bdec-2939-8845-c9a1fdb82cfc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-steps-for-restoring-the-forest.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-steps-for-restoring-the-forest
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-steps-for-restoring-the-forest.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d6dae808-ca74-47d3-28fa-fe3955c80c25
---

# AD Forest Recovery - Steps for Restoring the forest | Microsoft Learn

This section provides an overview of the recommended path for recovering a forest. The forest recovery steps are described in detail later.

We recommend you run through a forest recovery on a regular basis to:

- Practice the recovery.
- Ensure the custom steps you defined for your environment are still working.
- If steps don't work, you notice and update the existing plan to adopt for a new kind of potential failure.
- Verify the defaults you have for selecting the DCs to restore in each of the domains is still a good choice.

The following list summarizes the recovery steps at a high level:

1. [Identify the problem](ad-forest-recovery-identify-the-problem) Work with IT and Microsoft Support to determine the scope of the problem and potential causes, and evaluate possible remedies with all business stakeholders. In many cases, total forest recovery should be the last option.
2. [Determine how to recover the forest](ad-forest-recovery-determine-how-to-recover) After you determine that forest recovery is necessary, complete preliminary steps to prepare for it.
3. [Perform initial recovery](ad-forest-recovery-perform-initial-recovery) In isolation, recover one DC for each domain, clean it, and reconnect the domains. Reset privileged accounts, and rectify problems caused by security breaches in this phase.
4. [Redeploy remaining DCs](ad-forest-recovery-restore-additional-dcs) Redeploy the forest to return it to its state before the failure. Adapt this step to your specific design and requirements. Virtualized domain controller cloning can help expedite this process.
5. [Cleanup](ad-forest-recovery-cleanup) After functionality has been restored, reconfigure name resolution as needed, and get LOB applications working.

The steps in this guide are designed to minimize the possibility of reintroducing dangerous data into the recovered forest. You may have to modify these steps to account for such factors as:

- Scalability
- Remote manageability
- Speed of recovery