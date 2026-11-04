---
layout: Conceptual
title: AD Forest Recovery - Backing up a full server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-backing-up-a-full-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: A Bare Metal Recovery (BMR) backup is recommended to prepare for a forest recovery because it can be restored to different hardware or a different operating system instance. Using Windows Server Backup you can perform a Bare-Metal Recovery (BMR) backup of your server.
ms.author: roharwoo
author: robinharwood
ms.date: 2023-06-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: ef1b209d-369f-96ab-5c95-5b39262d55e1
document_version_independent_id: ef1b209d-369f-96ab-5c95-5b39262d55e1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-backing-up-a-full-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-backing-up-a-full-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-backing-up-a-full-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 61687dd1-313c-1803-b9dc-64962ac88c72
---

# AD Forest Recovery - Backing up a full server | Microsoft Learn

A Bare Metal Recovery (BMR) backup is recommended to prepare for a forest recovery because it can be restored to different hardware or a different operating system instance. Using Windows Server Backup you can perform a Bare-Metal Recovery (BMR) backup of your server.

## Windows Server Backup

Windows Server Backup isn't installed by default. In Windows Server 2012 R2, Windows Server 2016 and newer, install it by following the steps below.

Note

Please be aware that the steps may vary slightly between Windows Server 2012 R2 and Windows Server 2016+.

## Install Windows Server Backup

1. Open **Server Manager** and select **Add roles and features**.
2. On the **Add Roles and Features Wizard** select **Next**.
3. On the **Installation Type** screen, leave the default **Role-based or feature-based installation** and select **Next**.
4. On the **Server Selection** screen, select **Next**.
5. On the Server Roles screen, select **Next**.
6. On the **Features** screen, select **Windows Server Backup** and select **Next**![Screenshot that highlights the selected Windows Server Backup option.](media/a31518eb8f4ce532c957c9f4b61db202.png)
7. Select **Install**.
8. Once the installation is complete, select **Close**.

## Perform a backup with Windows Server Backup

1. Open **Server Manager**, select **Tools**, and then select **Windows Server Backup**. ![Screenshot that shows where to point to Administrative Tools and then select Windows Server Backup.](media/33f3c23bfe300f86cedcbf3f11c2c665.png)
2. If you're prompted, in the **User Account Control** dialog box, provide Backup Operator credentials, and then select **OK**.
3. Select **Local Backup**.
4. On the **Action** menu, select **Backup once**.
5. In the Backup Once Wizard, on the **Backup options** page, select **Different options**, and then select **Next**. ![Screenshot that shows the Different Options option selected.](media/3346c8870177678d27fdb4bffc1b9458.png)
6. On the **Select backup configuration** page, select **Full server (recommended)**, and then select **Next**. Or when you select “Custom”, make sure to select “Bare metal recovery” and the items is selected automatically:![Graphical user interface, text, application, email Description automatically generated](media/b88fe62fbfad14dbf54c0ef306b46dfc.png)
7. On the **Specify destination type** page, select **Local drives** or **Remote shared folder**, and then select **Next**.
8. On the **Select Backup Destination** page, choose the backup location. If you selected local drive choose a local drive or if you selected remote share choose a network share.
9. On the confirmation screen, select **Backup**. ![Screenshot that shows the Backup Progress screen.](media/16c2dff09f580d43a4b3d845a7b039f4.png)
10. Once this has completed select **Close**.
11. Close Windows Server Backup.

Note

If you get an error stating that no backup storage location is available, you will need to either exclude one of the volumes that has been selected or add a new volume or remote share. If you get a warning stating that the selected volume is also included in the list of items to backup, determine whether or not to remove and click **OK**.

## Use `wbadmin.exe` to back up a Windows Server

`Wbadmin.exe` is a command-line utility that enables you to back up and restore your operating system, volumes, files, folders, and applications from a command prompt.

## Perform a full server backup using `wbadmin.exe`

- Open an elevated command prompt, type the following command and press ENTER:

    For bare-metal backup:

    `wbadmin start backup -allCritical -backuptarget:\<Drive_letter_to_store_backup\>:`

    For full server backup:

    `wbadmin start backup -backuptarget:\<Drive_letter_to_store_backup\>: -include:\<Drive_letter_to_include\>:`

    ![Install backup](media/87bd3e26c885838443090c4ce7b7a04e.png)