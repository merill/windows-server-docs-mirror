---
layout: Conceptual
title: wbadmin | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wbadmin
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wbadmin commands, which lets you back up and restore your operating system, volumes, files, folders, and applications from a command prompt.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4bc546b0-5921-0353-974d-efcfd657b9fb
document_version_independent_id: b12ef9a2-f62c-96e7-778d-ea758551384a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wbadmin.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wbadmin
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wbadmin.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 9d0bd8cb-b9bf-11e1-778f-403048ef3039
---

# wbadmin | Microsoft Learn

Enables you to back up and restore your operating system, volumes, files, folders, and applications from a command prompt.

To configure a regularly scheduled backup using this command, you must be a member of the **Administrators** group. To perform all other tasks with this command, you must be a member of the **Backup Operators** group or the **Administrators** group, or you must have been delegated the appropriate permissions.

You must run **wbadmin** from an elevated command prompt, by right-clicking **Command Prompt**, and then selecting **Run as administrator**.

## Parameters

| Parameter | Description |
| --- | --- |
| [wbadmin delete catalog](wbadmin-delete-catalog) | Deletes the backup catalog on the local computer. Use this command only if the backup catalog on this computer is corrupted and you have no backups stored at another location that you can use to restore the catalog. |
| [wbadmin delete systemstatebackup](wbadmin-delete-systemstatebackup) | Deletes one or more system state backups. |
| [wbadmin disable backup](wbadmin-disable-backup) | Disables your daily backups. |
| [wbadmin enable backup](wbadmin-enable-backup) | Configures and enables a regularly scheduled backup. |
| [wbadmin get disks](wbadmin-get-disks) | Lists disks that are currently online. |
| [wbadmin get items](wbadmin-get-items) | Lists the items included in a backup. |
| [wbadmin get status](wbadmin-get-status) | Shows the status of the currently running backup or recovery operation. |
| [wbadmin get versions](wbadmin-get-versions) | Lists details of backups recoverable from the local computer or, if another location is specified, from another computer. |
| [wbadmin restore catalog](wbadmin-restore-catalog) | Recovers a backup catalog from a specified storage location in the case where the backup catalog on the local computer has been corrupted. |
| [wbadmin start backup](wbadmin-start-backup) | Runs a one-time backup. If used with no parameters, uses the settings from the daily backup schedule. |
| [wbadmin start recovery](wbadmin-start-recovery) | Runs a recovery of the volumes, applications, files, or folders specified. |
| [wbadmin start sysrecovery](wbadmin-start-sysrecovery) | Runs a recovery of the full system (at least all the volumes that contain the operating system's state). This command is only available if you are using the Windows Recovery Environment. |
| [wbadmin start systemstatebackup](wbadmin-start-systemstatebackup) | Runs a system state backup. |
| [wbadmin start systemstaterecovery](wbadmin-start-systemstaterecovery) | Runs a system state recovery. |
| [wbadmin stop job](wbadmin-stop-job) | Stops the currently running backup or recovery operation. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Windows Server Backup Cmdlets in Windows PowerShell](/en-us/powershell/module/windowsserverbackup)
- [Windows Recovery Environment (WinRE)](/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)