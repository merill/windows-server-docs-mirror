---
layout: Conceptual
title: Active Directory Forest Recovery - Identify the problem | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-identify-the-problem
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: When symptoms of a forest-wide failure appear, such as in event logs or other monitoring solutions, work with Microsoft Support to determine the cause of the failure and evaluate any possible remedies.
ms.author: roharwoo
author: robinharwood
ms.date: 2023-06-10T00:00:00.0000000Z
ms.topic: troubleshooting
locale: en-us
document_id: 663e46ac-f70f-38fc-6d9b-04d613a9305d
document_version_independent_id: 663e46ac-f70f-38fc-6d9b-04d613a9305d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-identify-the-problem.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-identify-the-problem
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-identify-the-problem.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: cd7d0bd9-ed95-7fe1-ebbc-b1bb3a8b0692
---

# Active Directory Forest Recovery - Identify the problem | Microsoft Learn

When symptoms of a forest-wide failure appear, such as in event logs or other monitoring solutions, work with Microsoft Support to determine the cause of the failure and evaluate any possible remedies.

Important

This guide doesn't cover security recommendations for how to recover a forest that has been hacked or compromised. In general, it's recommended to follow [Best Practices for Securing Active Directory](/en-us/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory) and Pass-the-Hash mitigation techniques to harden the environment. For more information, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft Techniques](https://www.microsoft.com/download/details.aspx?id=36036).

## Examples of forest-wide failures

- All DCs are logically corrupted or physically damaged to a point that business continuity is impossible; for example, all business applications that depend on AD DS aren't functional.
- A rogue administrator compromised the Active Directory environment.
- An attacker intentionally — or an administrator accidentally — runs a script that spreads data corruption across the forest.
- An attacker intentionally — or an administrator accidentally — extends the Active Directory schema with malicious or conflicting changes.
- The content, or a backup of a Domain Controller, has been exposed to an external party, but leaked credentials haven't been used to modify AD data. In this case, you may not need to restore the AD database from backup and reinstall all DCs. You may need to reset all password of users, computers, trusts and (g)MSA accounts.
- An attacker installed malicious software on DCs, and you were advised by Microsoft Support to recover the forest from backup.
- None of the DCs can replicate with their replication partners.
- Changes can't be made to AD DS at any domain controller.
- New DCs can't be installed in any domain.