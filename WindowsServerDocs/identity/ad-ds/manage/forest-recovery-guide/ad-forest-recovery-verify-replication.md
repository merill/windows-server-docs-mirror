---
layout: Conceptual
title: AD Forest Recovery - Verify Replication | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-verify-replication
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn more about resources to verify replication.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-09-25T00:00:00.0000000Z
locale: en-us
document_id: 80cd8d51-5c2d-ca10-ad03-9811cf60e62c
document_version_independent_id: 80cd8d51-5c2d-ca10-ad03-9811cf60e62c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-verify-replication.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-verify-replication
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-verify-replication.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: f792ba49-f6b2-5029-35a3-87eb2a4703c9
---

# AD Forest Recovery - Verify Replication | Microsoft Learn

After you've restored or reinstalled all domain controllers (DCs), you can verify that AD DS, and the sysvol folder has recovered and is replicating correctly by using `repadmin /replsum`. `repadmin /replsum` runs on any version of Windows Server.

Check the DFS Replication event logs for Event ID 4602 (or File Replication Service event ID 13516). This log event indicates sysvol replication has been initialized.

If the first recovered DC has Event ID 4614 in the DFS Replication log (“the domain controller is waiting to perform initial replication"), the replicated folder remains in the initial synchronization state until it has replicated with its partner. If Event ID 4602 doesn't appear, you need to perform the following manual steps to recover the sysvol folder if it's replicated using DFSR.

1. If DFSR Event 4612 appears on the first restored DC, perform a manual authoritative restore as described in [2218556: How to force authoritative and nonauthoritative synchronization for DFSR-replicated sysvol replication)](https://support.microsoft.com/kb/2218556).
2. Set **SysvolReady Flag** to 1 manually, as described in [947022 The NETLOGON share isn't present after you install Active Directory Domain Services on a new full or read-only Windows Server 2008-based domain controller](https://support.microsoft.com/kb/947022).

You can also create a diagnostic report DFS Replication. For more information, see [Create a Diagnostic Report for DFS Replication](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754227%28v=ws.11%29) and [DFS Step-by-Step Guide for Windows Server 2008](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754227%28v=ws.11%29). If the server is running Windows Server 2008 R2, you can use [dfsrdiag.exe ReplicationState command line switch](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754227%28v=ws.11%29).

You can also run the Replications test using dcdiag.exe to check for replication errors. For more information, see Knowledge Base [Active Directory replication error 8452 - Windows Server](/en-us/troubleshoot/windows-server/identity/replication-error-8452).