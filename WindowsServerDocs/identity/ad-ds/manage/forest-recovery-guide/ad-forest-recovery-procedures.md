---
layout: Conceptual
title: Active Directory Forest Recovery - Procedures | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-procedures
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: View a list of procedures that are used in backing up and restoring domain controllers and Active Directory.
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-09T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: b2acd7fc-5d0f-b772-3941-94057ef8838e
document_version_independent_id: b2acd7fc-5d0f-b772-3941-94057ef8838e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-procedures.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-procedures
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-procedures.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: ddee14d7-cd76-9c16-6433-5ee34054bedd
---

# Active Directory Forest Recovery - Procedures | Microsoft Learn

This section contains procedures related to the forest recovery process.

Following is a list of procedures that are used in backing up and restoring domain controllers and Active Directory.

- [Back up a full server](ad-forest-recovery-backing-up-a-full-server)
- [Back up the system state data](ad-forest-recovery-backing-up-system-state)
- [Perform a full server recovery](ad-forest-recovery-perform-full-server-recovery)
- [Perform an authoritative synch of DFSR-replicated SYSVOL](ad-forest-recovery-authoritative-recovery-sysvol)
- [Perform a nonauthoritative restore of Active Directory Domain Services](ad-forest-recovery-perform-nonauthoritative-restore)

These steps explain how to perform an authoritative restore of SYSVOL at the same time.

- [Configure the DNS Server service](ad-forest-recovery-configure-dns)
- [Remove the global catalog](ad-forest-recovery-remove-gc)
- [Increase the value of available RID pools](ad-forest-recovery-raise-rid-pool)
- [Invalidate the current RID pool](ad-forest-recovery-invaildate-rid-pool)
- [Seize an operations master role](ad-forest-recovery-seizing-operations-master-role)
- [Clean up after a restore](ad-forest-recovery-cleanup)
- [Clean the metadata of removed writable domain controllers](ad-forest-recovery-cleaning-metadata-of-removed-dcs)
- [Reset the computer account password of the domain controller](ad-forest-recovery-reset-computer-account-dc)
- [Reset the krbtgt password](ad-forest-recovery-reset-the-krbtgt-password)
- [Reset a trust password on one side of the trust](ad-forest-recovery-reset-trust)
- [Add the global catalog](ad-forest-recovery-add-gc)
- [Resources to verify replication is working](ad-forest-recovery-verify-replication)