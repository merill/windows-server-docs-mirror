---
layout: Conceptual
title: AD Forest Recovery - Backing up the System State data | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-backing-up-system-state
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD Forest Recovery - Backing up the System State data'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 9238cb27-0020-42f7-90d6-fcebf7e3c0bc, inhenkel
locale: en-us
document_id: 84bbc536-ec1f-f3b1-a76c-d5698c88fe6e
document_version_independent_id: 84bbc536-ec1f-f3b1-a76c-d5698c88fe6e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-backing-up-system-state.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-backing-up-system-state
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-backing-up-system-state.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 46a3f13a-58e6-eddc-60db-0107c456b5ee
---

# AD Forest Recovery - Backing up the System State data | Microsoft Learn

Use the following procedure to perform a system state backup on a Domain Controller (DC) by using Windows Server Backup or wbadmin.exe.

## Perform a system state backup using Windows Server Backup

1. Open **Server Manager**, select **Tools**, and then select **Windows Server Backup**.
    - In Windows Server 2008 R2 and Windows Server 2008, select **Start**, point to **Administrative Tools**, and then select **Windows Server Backup**. ![Screenshot that highlights the Windows Server Backup menu option.](media/fullbackup1.png)
2. If you're prompted, in the **User Account Control** dialog box, provide Backup Operator credentials, and then select **OK**.
3. Select **Local Backup**.
4. On the **Action** menu, select **Backup once**.
5. In the Backup Once Wizard, on the **Backup options** page, select **Different options**, and then select **Next**. ![Screenshot that shows the Backup Options page with the Different Options option selected.](media/fullbackup3.png)
6. On the **Select backup configuration** page, select **Custom**, and then select **Next**.
7. On the **Select Items for Backup** screen, select **Add Items** and select **System State** and select **Ok**.
    - In Windows Server 2008 R2 and Windows Server 2008, select the volumes to include in the backup. If you select the **Enable system recovery** check box, all critical volumes are selected. ![Screenshot that shows the System State check box selected.](media/systemstatebackup.png)
8. On the **Specify destination type** page, select **Local drives** or **Remote shared folder**, and then select **Next**. If you're backing up to a remote shared folder, do the following:
    - Type the path to the shared folder.
    - Under **Access Control**, select **Do not inherit** or **Inherit** to determine access to the backup, and then select **Next**.
    - In the **Provide user credentials for Backup** dialog box, provide the user name and password for a user who has write access to the shared folder, and then select **OK**.
9. For Windows Server 2008 R2 and Windows Server 2008, on the **Specify advanced option** page, select **VSS copy backup** and then select **Next**.
10. On the **Select Backup Destination** page, choose the backup location. If you selected local drive choose a local drive or if you selected remote share choose a network share.
11. On the confirmation screen, select **Backup**.
12. Once this has completed select **Close**.
13. Close Windows Server Backup.

## Perform a system state backup using Wbadmin.exe

Open an elevated command prompt, type the following command and press ENTER:

```cli
wbadmin start systemstatebackup -backuptarget:<targetDrive>:
```

![Install backup](media/systemstatebackup2.png)