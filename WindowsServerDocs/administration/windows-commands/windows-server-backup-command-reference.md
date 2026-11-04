---
layout: Conceptual
title: Windows Server Backup Command Reference | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/windows-server-backup-command-reference
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for backup command reference.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b7aae316-1481-67c6-80d6-2064153fe3ad
document_version_independent_id: 0045a29b-65c1-a529-03d1-d4828f41310b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/windows-server-backup-command-reference.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/windows-server-backup-command-reference
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/windows-server-backup-command-reference.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: d3a38349-5d0b-3d42-e305-aeb6d5023f54
---

# Windows Server Backup Command Reference | Microsoft Learn

The following subcommands for **wbadmin** provide backup and recovery functionality from a command prompt.

To configure a backup schedule, you must be a member of the **Administrators** group. To perform all other tasks with this command, you must be a member of the **Backup Operators** or the **Administrators** group, or you must have been delegated the appropriate permissions.

You must run **wbadmin** from an elevated command prompt. (To open an elevated command prompt, click **Start**, right-click **Command Prompt**, and then click **Run as administrator**.)

| Subcommand | Description |
| --- | --- |
| [Wbadmin enable backup](wbadmin-enable-backup) | Configures and enables a daily backup schedule. |
| [Wbadmin disable backup](wbadmin-disable-backup) | Disables your daily backups. |
| [Wbadmin start backup](wbadmin-start-backup) | Runs a one-time backup. If used with no parameters, uses the settings from the daily backup schedule. |
| [Wbadmin stop job](wbadmin-stop-job) | Stops the currently running backup or recovery operation. |
| [Wbadmin get versions](wbadmin-get-versions) | Lists details of backups recoverable from the local computer or, if another location is specified, from another computer. |
| [Wbadmin get items](wbadmin-get-items) | Lists the items included in a specific backup. |
| [Wbadmin start recovery](wbadmin-start-recovery) | Runs a recovery of the volumes, applications, files, or folders specified. |
| [Wbadmin get status](wbadmin-get-status) | Shows the status of the currently running backup or recovery operation. |
| [Wbadmin get disks](wbadmin-get-disks) | Lists disks that are currently online. |
| [Wbadmin start systemstaterecovery](wbadmin-start-systemstaterecovery) | Runs a system state recovery. |
| [Wbadmin start systemstatebackup](wbadmin-start-systemstatebackup) | Runs a system state backup. |
| [Wbadmin delete systemstatebackup](wbadmin-delete-systemstatebackup) | Deletes one or more system state backups. |
| [Wbadmin start sysrecovery](wbadmin-start-sysrecovery) | Runs a recovery of the full system (at least all the volumes that contain the operating system's state). This subcommand is only available if you are using the Windows Recovery Environment. |
| [Wbadmin restore catalog](wbadmin-restore-catalog) | Recovers a backup catalog from a specified storage location in the case where the backup catalog on the local computer has been corrupted. |
| [Wbadmin delete catalog](wbadmin-delete-catalog) | Deletes the backup catalog on the local computer. Use this command only if the backup catalog on this computer is corrupted and you have no backups stored at another location that you can use to restore the catalog. |