---
layout: Conceptual
title: Restore a virtualized domain controller in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/virtual-dc/restore-virtualized-domain-controller
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn about how to restore a virtualized Active Directory Domain Services Domain Controller (DC) in Windows Server.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-01-24T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 9ed46d4b-8194-dc04-1162-a89c62ecc085
document_version_independent_id: 9ed46d4b-8194-dc04-1162-a89c62ecc085
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/virtual-dc/restore-virtualized-domain-controller.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/virtual-dc/restore-virtualized-domain-controller
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/virtual-dc/restore-virtualized-domain-controller.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 988497a1-1fd0-154e-1d8a-c33444c22f97
---

# Restore a virtualized domain controller in Windows Server | Microsoft Learn

You must regularly back up your system state in order to restore a physical or virtual domain controller (DC) during a disaster recovery scenario. The system state includes Active Directory data and log files, the registry, the system volume, and various elements of the operating system. Active Directory-compatible backup applications ensure consistent local and replicated Active Directory databases after a restore process, including notifying replication partners of invocation ID resets. Virtual hosting environments and disk or OS imaging applications let administrators bypass standard checks and validations that occur during DC system state restore.

If your DC virtual machine (VM) fails, and you don't see signs of an [update sequence number (USN) rollback](../../get-started/virtual-dc/virtualized-domain-controllers-hyper-v#usn-and-usn-rollback), there are two ways you can restore the VM:

- If your system has a valid system state data backup from before the failure, you can restore it using the Active Directory-compatible backup utility you used to create the backup within the tombstone lifetime. The default tombstone lifetime is 180 days. You should back up your DCs regularly and at least every 90 days. For more information about determining tombstone lifetimes, see [Determine the tombstone lifetime for the forest](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc784932%28v=ws.10%29).
- If you have a working copy of the virtual hard disk (VHD) file but no system state backup, you can remove the existing VM and restore it using a previous copy of the VHD. Make sure to start the VM in DSRM, then configure the registry property as described in Restore a system state backup. After that, restart the DC in normal mode.

## Determine the best way to back up your DC

There are several ways to back up your DC, but which way works best for your deployment depends on multiple factors.

- If you don't have critical data on the DC or don't have a backup made before the DC went down:

    - Forcibly remove the AD DS role from the DC.
    - Remove the failed domain controller's computer account.
    - If necessary, install the AD DS role on the replacement server that becomes the next DC.
- If you have a system state backup, restore the DC by following the instructions in Restore a system state backup.
- If you have a previous version of the DC on a VHD file, follow the directions in Restore the virtual DC with a VHD file.

    - If the previous version runs Windows Server 2012 on a Hyper-V that supports the VM-GenerationID parameter, then deploy the VHD against a new VM, then restart the VM in normal mode.
    - If the previous version runs a different version of Windows Server, have you already started it in normal mode?

        - If no, then restore the DC by starting it in DSRM, setting the database restored from backup registry value to 1, then restarting it in normal mode.
        - If yes, disconnect the virtual DC from the network, recover, and save any required unique data on a different copy of the VM, then don't use the original DC on the network again. Also, remove its AD DS role from original DC or reinstall the OS, then install the role to the new version of the DC.

If you're trying to restore an RODC:

- If there's a system state data backup from before the original DC failed, use it to restore the DC.
- If you don't have a system state backup but you do have a VHD file of a previous version of the DC, remove the failed DC, then create and start a new VM using the backup from the VHD file.
- If you don't have either of those backups, remove the AD DS role from the domain controller by running this command:

    ```cmd
    dcpromo /forceremoval
    ```

    After running the command, install the AD DS role on the replacement server to make it an RODC.

## Restore a system state backup

If a valid system state backup exists for the DC VM, you can safely restore the backup by following the restore procedure for the backup tool that you used to back up the VHD file.

Important

To properly restore the DC, you must start the DC in DSRM, not normal mode. If you miss the opportunity to enter DSRM during system startup, turn off the DC's VM before it can fully start in normal mode. It's important to start the DC in DSRM because starting a DC in normal mode increments the USNs, even if the DC is disconnected from the network. For more information about USN rollback, see [USN and USN rollback](../../get-started/virtual-dc/virtualized-domain-controllers-hyper-v#usn-and-usn-rollback).

### Restore the system state backup of the virtual DC

To restore the system state data backup of the virtual DC:

1. Start the DC's VM, then press the F5 key to access **Windows Boot Manager**.
2. If you're prompted to enter connection credentials, follow these steps:

    - Immediately select the **Pause** button on the VM to pause the process.
    - Enter your connection credentials.
    - Select the **Play** button on the VM.
    - Select inside the VM window, and press the F5 key.

    If **Windows Boot Manager** doesn't open and the DC begins to start in normal mode, turn the VM off to pause the process. Repeat this step as many times as necessary until you're able to access Windows Boot Manager. You can't access DSRM from the Windows Error Recovery menu. Therefore, turn off the VM and try again if the Windows Error Recovery menu appears.
3. In **Windows Boot Manager**, press the F8 key to access advanced boot options.
4. Under **Advanced Boot Options**, select **Directory Services Restore Mode**, and then press the Enter key to start the DC in DSRM.
5. Use the appropriate restore method for the tool that you used to create the system state backup. If you used Windows Server Backup, follow the directions in [Performing a nonauthoritative restore of AD DS](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730683%28v=ws.10%29).

### Restore the virtual DC with a VHD file

If you don't have a system state data backup that predates the VM failure, you can use the VHD file to restore a DC that's running on a VM. Make sure you create a copy of the VHD file before you start. That way, if you encounter an issue during the procedure or miss a step, you can try again with the copied VHD.

Warning

You shouldn't use this procedure as a substitute for regularly planned and scheduled backups. Restores performed with this procedure aren't supported by Microsoft. Use this procedure only when there's no alternative.

Don't use this procedure if any VM has already started the copy of the VHD you plan to use for the restoration in normal mode.

To restore a virtual DC with a VHD file:

1. Using the previous VHD, start the virtual DC in DSRM.

    - Don't start the DC in normal mode. If you miss the **Windows Boot Manager** screen and the DC begins to start in normal mode, turn the VM off to prevent it from starting up.
2. Open the Registry Editor by selecting **Start**, then entering `regedit.exe` and selecting **Registry Editor**.

    - If the **User Account Control** dialog displays, confirm the displayed action is as expected, then select **Yes**.
    - In Registry Editor, expand the path `HKLM\SYSTEM\CurrentControlSet\Services\NTDS\Parameters`.
    - Look for a value named **DSA Previous Restore Count**. If the value is present, make a note of the setting. Otherwise, the setting value is the default (0). If no value is shown, don't manually set the value.
3. Right-click the **Parameters** key, select **New**, and then select **DWORD (32-bit) Value**.
4. Enter the new name **Database restored from backup**, then press the Enter key.
5. Double-click the value you just created to open the **Edit DWORD (32-bit) Value** dialog, then find the **Value data** field and enter **1**.
6. Restart the DC in normal mode.
7. When the DC restarts, open Event Viewer by right-clicking **Start**, then selecting **Event Viewer**.
8. Expand **Application and Services Logs**, then select the **Directory Services** log. Ensure the events appear in the details pane.
9. Right-click the **Directory Services** log, then select **Find**.
10. In the **Find what** field, enter **1109**, then select **Find Next**.
11. You should see at least one entry for Event ID 1109. If you don't see this entry, proceed to the next step. Otherwise, double-click the entry and review the text. Confirm the text shows that the update was made to the InvocationID, as shown in the following example output:

    ```output
    Active Directory has been restored from backup media, or has been configured to host an application partition.
    The invocationID attribute for this directory server has been changed.
    The highest update sequence number at the time the backup was created is <time>
    
    InvocationID attribute (old value):<Previous InvocationID value>
    InvocationID attribute (new value):<New InvocationID value>
    Update sequence number:<USN>
    
    The InvocationID is changed when a directory server is restored from backup media or is configured to host a writeable application directory partition.
    ```
12. Close **Event Viewer**.
13. Use **Registry Editor** to verify the value for the **DSA Previous Restore Count** setting is equal to the previous value plus one. If the correct value isn't there and you can't find an entry for Event ID 1109 in **Event Viewer**, verify that the DC's service packs are current.

    Note

    You can't try this procedure again on the same VHD. You can try again on a copy of the VHD or a different VHD that hasn't been started in normal mode by starting again from step 1.
14. Close the **Registry Editor**.

## Additional content

For more information about virtualized DCs, see [Virtualizing domain controllers with Hyper-V](../../get-started/virtual-dc/virtualized-domain-controllers-hyper-v).