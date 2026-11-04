---
layout: Conceptual
title: AD Forest Recovery - Performing a full server recovery | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-perform-full-server-recovery
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: A full server recovery is necessary if you're restoring to different hardware or a different operating system instance. Bare-Metal recovery is a supported method of backup.
ms.author: roharwoo
author: robinharwood
ms.date: 2023-06-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 87f80e67-f325-f30e-77ae-5078bd74cef8
document_version_independent_id: 87f80e67-f325-f30e-77ae-5078bd74cef8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-perform-full-server-recovery.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-perform-full-server-recovery
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-perform-full-server-recovery.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 467bee00-834b-ecb8-e7bd-03d7dc0ce5a0
---

# AD Forest Recovery - Performing a full server recovery | Microsoft Learn

## Active Directory Full Server Recovery

A full server recovery is necessary if you're restoring to different hardware or a different operating system instance. Bare-Metal recovery is a supported method of backup.

Keep in mind the following:

- The number drives on the target server needs to be equal to the number in the backup and they need to be the same size or greater.
- The target server needs to be started from the operating system DVD in order to access Windows PE Environment, and using the **Repair your computer** option.
- If you're using disk volume encryption solutions like BitLocker, make sure you test and apply the steps necessary to the server recovery plan for getting the server OS restored and started properly.
- If the target DC is running in a VM on Hyper-V and the backup is stored on a network location, you must install a legacy network adapter, with all isolation precautions needed depending on your recovery scenario.
- After you perform a full server recovery, you need to separately perform an authoritative restore of SYSVOL, as described in [AD Forest Recovery - Performing an authoritative synchronization of DFSR-replicated SYSVOL](ad-forest-recovery-authoritative-recovery-sysvol).

Depending on your scenario, use one of the following procedures to perform a full restore.

**Perform a full server restore with a healthy local backup using the latest image**

1. Start Windows Setup, specify the Language, Time and currency format, and keyboard options and select **Next**.
2. Select **Repair your computer**. ![Screenshot that shows where to select Repair your computer.](media/553721c65252ea0a039ff206a8bf43bb.png)
3. Select **Troubleshoot**.![Screenshot that shows the Troubleshoot option.](media/1cb2ace61dcdf29fb39fceb5309c5376.png)
4. Select **System Image Recovery**.![Screenshot that shows the System Image Recovery option.](media/dbc1f945041dca0edb7967de8907d726.png)
5. Select **Windows Server 2016**. ![Screenshot that shows the Windows Server 2016 option.](media/799b14685522d334e3bba855a025e94a.png)
6. If you're restoring the most recent local backup, select **Use the latest available system image (recommended)** and select **Next**. 
    Note

    If you need to select a backup from another time as the problem was introduced was introduced some time ago, select "Select a system image" and chose the known good backup. ![Screenshot that shows the Use the latest available system image (recommended) option.](media/6fed751a5b8ca6c0b343cbb3fc8679c5.png)
7. You'll now be given an option to:
    - Format and repartition disks.
    - Install drivers.
    - Deselecting the **Advanced** features of automatically restarting and checking for disk errors. These are enabled by default. ![Screenshot that highlights the Advanced... button.](media/66a6821db9ede980c7c1ae615a9d3128.png)
8. Select **Next**.
9. Select **Finish**. You'll be prompted if you're sure you want to continue. Select **Yes**. ![Screenshot that shows the progress of the image restoration.](media/379d865f820f6d2fa20f0d78c283bc87.png)
10. Once this completes, perform an authoritative restore of SYSVOL, as described in [AD Forest Recovery - Performing an authoritative synchronization of DFSR-replicated SYSVOL](ad-forest-recovery-authoritative-recovery-sysvol).

## Perform a full server restore with any image local or remote

1. Start Windows Setup, specify the Language, Time and currency format, and keyboard options and select **Next**.
2. Select **Repair your computer**.
3. Select **Troubleshoot**, select **System Image Recovery**, and select **Windows Server 2016**.
4. If you're restoring the most recent local backup, select **Select a system image** and select **Next**.
5. Now you can select the location of the backup that you want to restore. If the image is local, you can select it from the list.
6. If the image is on a network share, select **Advanced**. You can also select **Advanced** if you need to install a driver. ![Screenshot that highlights the Advanced button in the Re-image your computer dialog box.](media/dffb0ae6bfebd201e0c2b6b947df034d.png)
7. If you're restoring from the network after clicking **Advanced** select **Search for a system image on the network**. You may be prompted to restore network connectivity. Select Ok.![Screenshot that highlights the Search for a system image on the network option.](media/e07bdbc646362ef4642b9994e96c5e69.png)
8. Type the UNC path to the backup share location (for example, `\\\\server1\\backups`) and select **OK**. You can also type the IP address of the target server, such as `\\\\192.168.1.3\\backups`. ![Server Restore](media/e08571ed9738be2cac0b352213c80353.png)
9. Type credentials necessary to access the share and select OK.
10. Now **Select the date and time of system image to restore** and select **Next**.
11. You'll now be given an option to:
    - Format and repartition disks.
    - Install drivers.
    - Deselecting the **Advanced** features of automatically restarting and checking for disk errors. These are enabled by default.
12. Select **Next**.
13. Select **Finish**. You'll be prompted asking if you're sure you want to continue. Select **Yes**.
14. Once this completes, perform an authoritative restore of SYSVOL, as described in [AD Forest Recovery - Performing an authoritative synchronization of DFSR-replicated SYSVOL](ad-forest-recovery-authoritative-recovery-sysvol).

## Enable the network adapter for a network backup

If you need to enable a network adapter from the command prompt to restore from a network share, use the following steps.

1. Start Windows Setup, specify the Language, Time and currency format, and keyboard options and select **Next**.
2. Select **Repair your computer**. I
3. Select **Troubleshoot**, select **Command Prompt**.
4. Type the following command and press ENTER: `wpeinit`
5. To confirm the name of the network adapter, type: `show interfaces`
6. Type the following commands and press ENTER after each command: `netsh``interface``tcp``ipv4``set address "Name of Network Adapter" static IPv4 Address SubnetMask IPv4 Gateway Address 1`

    For example:

    `set address "Local Area Connection" static 192.168.1.2 255.0.0.0 192.168.1.1 1`
7. Type `quit` to return to a command prompt.
8. Type `ipconfig /all` to verify the network adapter has an IP address and try to ping the IP address of the server that hosts the backup share to confirm connectivity.
9. Close the command prompt when you're done.
10. Now that the network adapter is working, repeat the steps above to complete the restore.