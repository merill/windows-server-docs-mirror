---
layout: Conceptual
title: Active Directory Forest Recovery - Performing a nonauthoritative restore of Active Directory Domain Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-perform-nonauthoritative-restore
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: The following procedures use the wbadmin.exe to perform a nonauthoritative restore of Active Directory or Active Directory Domain Services (AD DS). If you're using a different backup solution or if you intend to complete the authoritative restore of SYSVOL later in the forest recovery process...
perform an authoritative restore of SYSVOL by using these alternative methods: 
ms.author: roharwoo
author: robinharwood
ms.date: 2023-06-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 4b50b719-94fb-d4b2-acfd-b89f745b556f
document_version_independent_id: 4b50b719-94fb-d4b2-acfd-b89f745b556f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-perform-nonauthoritative-restore.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-perform-nonauthoritative-restore
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-perform-nonauthoritative-restore.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: da37035c-816d-0a76-e95b-00e8083f8bb6
---

# Active Directory Forest Recovery - Performing a nonauthoritative restore of Active Directory Domain Services | Microsoft Learn

To perform a nonauthoritative restore, complete the following procedure.

The following procedures use the wbadmin.exe to perform a nonauthoritative restore of Active Directory or Active Directory Domain Services (AD DS). If you're using a different backup solution or if you intend to complete the authoritative restore of SYSVOL later in the forest recovery process, you can perform an authoritative restore of SYSVOL by using these alternative methods:

- Determine if SYSVOL is replicated by FRS, see [Determining Whether a Domain Controller's SYSVOL Folder is Replicated by DFSR or FRS](/en-us/windows/win32/vss/backing-up-and-restoring-an-frs-replicated-sysvol-folder#determining_whether_a_domain_controller_s_sysvol_folder_is_replicated_by_dfsr_or_frs).
- If you're still using File Replication Service (FRS), please consider switching to Distributed File System (DFS) Replication as soon as possible. If you still use FRS to replicate SYSVOL, follow the steps in [article 290762](/en-us/troubleshoot/windows-server/networking/use-burflags-to-reinitialize-frs) in the Microsoft Knowledge Base, using the **BurFlags** registry key to reinitialize FRS replica sets, or if necessary, article [315457](https://support.microsoft.com/kb/315457) to rebuild the SYSVOL tree.
- If you're using Distributed File System (DFS) Replication to replicate SYSVOL, see [Perform an authoritative synchronization of DFSR-replicated SYSVOL](ad-forest-recovery-authoritative-recovery-sysvol).

## Perform a nonauthoritative restore

Use the following procedure to perform a nonauthoritative restore of AD DS and an authoritative restore of SYSVOL at the same time by using wbadmin.exe. The backup must explicitly include system state data; a full server backup that is used for full server recovery won't work. A Bare Metal Recovery Backup (BMR) will contain a system state backup. For more information about creating a system state backup, see [Backing up the System State data](ad-forest-recovery-backing-up-system-state).

### Perform a nonauthoritative restore of AD DS and authoritative restore of SYSVOL using wbadmin.exe\*\*

Include the **-authsysvol** switch in your recovery command, as shown in the following example:

`wbadmin start systemstaterecovery \<otheroptions\> -authsysvol`

For example:

`wbadmin start systemstaterecovery -version:01/01/2023-13:00 -authsysvol`

![Restore](media/b81604238b4288f9fac4e3f791d82e5f.png)