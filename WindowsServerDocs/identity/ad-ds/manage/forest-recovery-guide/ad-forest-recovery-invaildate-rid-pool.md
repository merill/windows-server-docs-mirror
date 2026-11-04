---
layout: Conceptual
title: AD Forest Recovery - Invalidating the RID Pool | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-invaildate-rid-pool
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD Forest Recovery - Invalidating the current RID pool'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 4b511f61-b64c-96b4-a6a6-46ed0aa7d248
document_version_independent_id: 4b511f61-b64c-96b4-a6a6-46ed0aa7d248
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-invaildate-rid-pool.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-invaildate-rid-pool
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-invaildate-rid-pool.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d17b4ca6-be23-08bc-6c71-dba4487e364f
---

# AD Forest Recovery - Invalidating the RID Pool | Microsoft Learn

Use the following procedure to use Windows PowerShell to invalidate the current RID pool on a domain controller. Windows PowerShell is enabled by default on Windows Server 2012 and Windows Server 2008 R2, but not Windows Server 2008 where it must be installed by using **Add Features**. It can be [downloaded](/en-us/troubleshoot/windows-server/system-management-components/windows-server-2003-service-pack-1-support-tools) to run on Windows Server 2003.

To verify the command completed successfully, check for event ID 16654 (source is Directory-Services-SAM) in the System log in Event Viewer in Windows Server 2012. Earlier versions of Windows don't log this event.

Note

After you invalidate the RID pool, you will receive an error when you first attempt to create security principal (user, computer, or group). The attempt to create an object triggers a request for a new RID pool. Retry of the operation succeeds because the new RID pool will be allocated.

## Invalidate the current RID pool

- Open an elevated Windows PowerShell session, run the following command and press ENTER:

    ```powershell
    $Domain = New-Object System.DirectoryServices.DirectoryEntry
    $DomainSid = $Domain.objectSid
    $RootDSE = New-Object System.DirectoryServices.DirectoryEntry("LDAP://RootDSE")
    $RootDSE.UsePropertyCache = $false
    $RootDSE.Put("invalidateRidPool", $DomainSid.Value)
    $RootDSE.SetInfo()
    ```