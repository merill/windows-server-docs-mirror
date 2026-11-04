---
layout: Conceptual
title: Migrate SYSVOL replication from FRS to DFS Replication | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/dfs-replication/migrate-sysvol-to-dfsr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how to migrate SYSVOL replication from File Replication Service (FRS) to Distributed File System Replication (DFSR). Follow this step-by-step guide to ensure a smooth transition and improve your Active Directory reliability.
author: robinharwood
ms.author: roharwoo
ms.topic: upgrade-and-migration-article
ms.date: 2025-05-14T00:00:00.0000000Z
locale: en-us
document_id: 1999621a-92cd-28d0-88e0-c504d409afa5
document_version_independent_id: a9c96c5f-b03d-1805-fd7d-29853d33d03c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/dfs-replication/migrate-sysvol-to-dfsr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/dfs-replication/migrate-sysvol-to-dfsr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/dfs-replication/migrate-sysvol-to-dfsr.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 34cf4660-d113-006c-2baa-f1c2429919e2
---

# Migrate SYSVOL replication from FRS to DFS Replication | Microsoft Learn

Active Directory domain controllers use a special shared folder named `SYSVOL` to replicate sign-in scripts and Group Policy object files to other domain controllers. Windows 2000 Server and Windows Server 2003 used the File Replication Service (FRS) to replicate the `SYSVOL` folder and its contents. Current versions of Windows Server use the newer Distributed File System Replication (DFS Replication) service, which was introduced in Windows Server 2008, for domains that use the Windows Server 2008 domain functional level or later. Windows Server 2008 uses FRS for domains that run older domain functional levels.

If you're running a domain that uses FRS, you can migrate the replication of the `SYSVOL` folder to use DFS Replication. This migration is a one-way process. After you migrate to DFS Replication, you can't revert to FRS.

This article provides a guide to help you migrate the `SYSVOL` folder from FRS to DFS Replication. The migration process is complex and requires careful planning and execution. The guide includes information about the migration process, prerequisites, and procedures.

## Prerequisites

This article assumes you have a basic knowledge of Active Directory Domain Services (AD DS), FRS, and Distributed File System Replication (DFS Replication). For more information, see:

- [Active Directory Domain Services overview](/en-us/previous-versions/orphan-topics/ws.11/cc731053%28v=ws.11%29)
- [FRS overview](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754297%28v=ws.11%29)
- [Overview of DFS Replication](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771058%28v=ws.11%29)

## Printable download

To download a printable version of this guide, go to [SYSVOL Replication Migration Guide: FRS to DFS Replication](https://go.microsoft.com/fwlink/?LinkId=150375).

## Migration articles

The SYSVOL migration guide provides articles that describe a range of concepts and procedures from the use of FRS to the use DFS. Use the following list to access articles about migrating the SYSVOL folder to use DFS Replication.

### Concepts

Review these concepts about SYSVOL migration states for a basic understanding of the migration tasks.

- [SYSVOL migration conceptual information](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd640170%28v=ws.10%29)
- [SYSVOL migration states](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd641052%28v=ws.10%29)
- [Overview of the SYSVOL migration procedure](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd639809%28v=ws.10%29)

### Procedures

Follow these SYSVOL migration procedures for a basic understanding of the migration states.

- [SYSVOL migration procedure](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd639860%28v=ws.10%29)
- [Migrate to the Prepared state](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd641193%28v=ws.10%29)
- [Migrate to the Redirected state](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd641340%28v=ws.10%29)
- [Migrate to the Eliminated state](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd640254%28v=ws.10%29)

### Troubleshooting

Access these articles that describe known issues and provide troubleshooting guidance.

- [Troubleshooting SYSVOL migration](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd640395%28v=ws.10%29)
- [Troubleshooting SYSVOL migration issues](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd639976%28v=ws.10%29)
- [Rolling back SYSVOL migration to a previous stable state](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd640509%28v=ws.10%29)

### References

The following resources offer supplemental reference information:

- [SYSVOL migration reference information](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd640293%28v=ws.10%29)
- [Supported SYSVOL migration scenarios](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd639854%28v=ws.10%29)
- [Verifying the state of SYSVOL migration](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd639789%28v=ws.10%29)
- [Dfsrmig](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd641227%28v=ws.10%29)
- [SYSVOL migration tool actions](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd639712%28v=ws.10%29)

## Related links

- [SYSVOL Migration Series: Part 1 – Introduction to the SYSVOL migration process](https://techcommunity.microsoft.com/t5/storage-at-microsoft/sysvol-migration-series-part-1-8211-introduction-to-the-sysvol/ba-p/423456)
- [SYSVOL Migration Series: Part 2 – Dfsrmig.exe: The SYSVOL migration tool](https://techcommunity.microsoft.com/t5/storage-at-microsoft/sysvol-migration-series-part-2-8211-dfsrmig-exe-the-sysvol/ba-p/423470)
- [SYSVOL Migration Series: Part 3 - Migrating to the 'PREPARED' state](https://techcommunity.microsoft.com/t5/storage-at-microsoft/sysvol-migration-series-part-3-migrating-to-the-prepared-state/ba-p/423503)
- [SYSVOL Migration Series: Part 4 – Migrating to the 'REDIRECTED' state](https://techcommunity.microsoft.com/t5/storage-at-microsoft/sysvol-migration-series-part-4-8211-migrating-to-the-8216/ba-p/423514)
- [SYSVOL Migration Series: Part 5 – Migrating to the 'ELIMINATED' state](https://techcommunity.microsoft.com/t5/storage-at-microsoft/sysvol-migration-series-part-5-8211-migrating-to-the-8216/ba-p/423516)
- [Distributed File System step-by-step guide for Windows Server 2008](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732863%28v=ws.10%29)
- [FRS technical reference](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc759297%28v=ws.10%29)