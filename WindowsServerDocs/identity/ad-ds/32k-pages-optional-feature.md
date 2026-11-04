---
layout: Conceptual
title: Database 32k pages for Active Directory on Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/32k-pages-optional-feature
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn about Database 32k page optional feature for Active Directory Domain Services and Active Directory Lightweight Domain Services on Windows Server.
author: robinharwood
ms.author: roharwoo
ms.date: 2024-10-25T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: b9efcd17-fb3d-6857-b32a-be563b662695
document_version_independent_id: b9efcd17-fb3d-6857-b32a-be563b662695
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/32k-pages-optional-feature.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/32k-pages-optional-feature
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/32k-pages-optional-feature.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 5e5524ea-b27d-f1b3-4696-dd644cf24c11
---

# Database 32k pages for Active Directory on Windows Server | Microsoft Learn

Active Directory Domain Services (AD DS) and Lightweight Directory Services (LDS) uses an [Extensible Storage Engine (ESE) database](/en-us/windows/win32/extensible-storage-engine/extensible-storage-engine-files). Since its introduction in Windows 2000, ESE used an 8k page database size, this architecture limited the scale of forest and domain objects. A 32k page database format offers an improvement in scalability using 64-bit [Long Value IDs](/en-us/windows/win32/extensible-storage-engine/long-value-columns) (LIDs). Multi-valued attributes are now able to hold approximately 3,200 values. For more information about Active Directory's scalability, see [Active Directory Maximum Limits - Scalability](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc756101%28v=ws.10%29).

To learn more about the ESE database, see [ESE Deep Dive: Part 1: The Anatomy of an ESE database](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/ese-deep-dive-part-1-the-anatomy-of-an-ese-database/ba-p/400496).

Beginning with Windows Server 2025, new installs of Active Directory Domain Services (AD DS) and Lightweight Directory Services (LDS) use a 32k page database format.

New AD forest, domains, or LDS instances are installed with a 32k page capable database but use an 8k page simulation mode for compatibility with earlier AD DS and LDS instances. Moving to a 32k database page-size is a forest-wide operation and requires that all domain controllers in the forest have a 32k page capable database.

Important

Domain controllers that have had a Feature Update, also known as an in-place upgrade, continue to their current 8K page database format and pages.

## Requirements

Before you can enable the *Database 32k pages optional feature* in your Active Directory Domain Services, your environment needs to meet the following requirements.

- Your Active Directory forest and domain is operational and free from replication errors. To learn more about replication errors, see [Diagnose Active Directory replication failures](/en-us/troubleshoot/windows-server/active-directory/diagnose-replication-failures).
- All domain controllers are running Windows Server 2025 or later, and have a 32k page capable database.
- Domain and forest functional levels are upgraded to Windows Server 2025 or later. To learn more about raising the functional levels, see [Raise Active Directory domain and forest functional levels](/en-us/troubleshoot/windows-server/active-directory/raise-active-directory-domain-forest-functional-levels).
- Identify all your DCs hosting the Global Catalog (GC) and FSMO roles. Create and verify backups of these Active Directory Domain Services domain controllers before making changes.
- Validate your backup software is compatible with the 32k page database format by backing up and restoring a 32k page capable database in a test environment.

## Considerations

When you create a backup of an AD database, the page size of the database is preserved on a backup media. Before Windows Server 2025, all backup media used 8k-page databases, which was the only page size supported. However, a server running Windows Server 2025 or later might have either an 8k or 32k page database format in 8k page simulation mode. For example, a Windows Server 2025 machine might have an 8K page database if it was in-place upgraded from an earlier version. It might have a 32k page database format in 8k page simulation mode if it was:

- Installed as a new DC in a Windows Server 2025 forest.
- Promoted to a DC over-the-wire. For example, promoted as a new replica.
- Restored from a 32k page database format backup image.

Before you enable the Database 32k pages optional feature, you can use either 8k or 32k page database format backup media to restore a Windows Server 2025 domain controller. After you enable the Database 32k pages optional feature, you can only use 32k page database format backup media to restore a Windows Server 2025 domain controller. You should also consider that enabling the larger 32k page sizes can affect server performance due to increased memory usage.

Warning

Once you have enabled the Database 32k pages optional feature, you can't revert back to the previous 8k page simulation mode. As a result, any 8k-page backup media created prior to enabling the feature will be unusable unless you perform a complete authoritative forest recovery.