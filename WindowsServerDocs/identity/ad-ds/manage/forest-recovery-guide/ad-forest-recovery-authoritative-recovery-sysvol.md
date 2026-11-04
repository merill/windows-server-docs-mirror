---
layout: Conceptual
title: AD Forest Recovery - Performing an authoritative synchronization of DFSR-replicated SYSVOL | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-authoritative-recovery-sysvol
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: There are different ways to perform an authoritative restore of SYSVOL. You can either edit the **msDFSR-Options** attribute or perform a system state restore using wbadmin –authsysvol. If you have the option to restore a system state backup (that is, you're restoring AD DS to the same hardware and operating system instance) then using wbadmin –authsysvol is simpler. But if you need to perform a bare metal restore, then you need to edit the **msDFSR-Options** attribute.
ms.author: roharwoo
author: robinharwood
ms.date: 2023-06-21T00:00:00.0000000Z
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: c4008fcc-cecb-5027-c8ae-a32ca7d4519a
document_version_independent_id: c4008fcc-cecb-5027-c8ae-a32ca7d4519a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-authoritative-recovery-sysvol.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-authoritative-recovery-sysvol
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-authoritative-recovery-sysvol.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 3634d8d3-8056-e764-23a1-a9319eea3e6a
---

# AD Forest Recovery - Performing an authoritative synchronization of DFSR-replicated SYSVOL | Microsoft Learn

There are different ways to perform an authoritative restore of SYSVOL. You can either edit the **msDFSR-Options** attribute or perform a system state restore using wbadmin –authsysvol. If you have the option to restore a system state backup (that is, you're restoring AD DS to the same hardware and operating system instance) then using wbadmin –authsysvol is simpler. But if you need to perform a bare metal restore, then you need to edit the **msDFSR-Options** attribute.

Use the following steps to perform an authoritative synchronization of SYSVOL (if it's replicated using DFSR) by editing the **msDFSR-Options** attribute. Note it can also be done using PowerShell.

**To perform an authoritative synchronization of DFSR-replicated SYSVOL using Active Directory Users and Computers**

1. Open Active Directory Users and Computers.
2. Select **View**, and then select **Users, Contacts, Groups, and Computers as containers** and **Advanced Features**. ![Screenshot that shows the Advanced Features option and Users, Contacts, Groups, and Computers option selected.](media/2a596a72680c054e00119332adab55d8.png)
3. In the tree-view, select **Domain Controllers**, the name of the DC you restored, **DFSR-LocalSettings**, and then **Domain System Volume**. ![Screenshot that highlights the Domain System Volume folder.](media/ce6e4c2fa09ce87da6eab16028af486b.png)
4. In the Details pane, right-click **SYSVOL Subscription**, select **Properties**, and select **Attribute Editor**. ![Screenshot that shows the Attribute Editor tab in the SYSVOL Subscriptions Properties dialog box.](media/3433980453db8591e0b34f9cb3c93d1c.png)
5. Select **msDFSR-Options**, select **Edit**, type **1**, and select **OK**.
6. Select **OK** to close the Attribute Editor.

## Verify if the authoritative restore is successful using PowerShell

1. After the previous operation, restart the DFSR service:

    **Restart-Service DFSR -PassThru**![Restart the DFSR service.](media/18334b3759684f7f38a711e2a5c59337.png)
2. Verify the presence if Event ID 4602

    **Get-WinEvent -LogName 'DFS Replication' | Where-Object ID -EQ 4602 | Format-Table -AutoSize -Wrap**![Verify the present of Event ID](media/2352605524b280902670023231454ca6.png)