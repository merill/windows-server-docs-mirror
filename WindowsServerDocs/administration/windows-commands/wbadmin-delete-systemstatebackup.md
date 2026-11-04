---
layout: Conceptual
title: wbadmin delete systemstatebackup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wbadmin-delete-systemstatebackup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wbadmin delete systemstatebackup command, which deletes the system state backups that you specify.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 3d61fe7f-1576-54f9-cfd8-2c065cf4353a
document_version_independent_id: 879f4d16-4fab-7cb6-c84d-53ac717c7e1e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wbadmin-delete-systemstatebackup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wbadmin-delete-systemstatebackup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wbadmin-delete-systemstatebackup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 7aff007c-85e2-d09b-37cb-7f407ff42790
---

# wbadmin delete systemstatebackup | Microsoft Learn

Deletes the system state backups that you specify. If the specified volume contains backups other than system state backups of your local server, those backups will not be deleted.

To delete a system state backup using this command, you must be a member of the **Backup Operators** group or the **Administrators** group, or you must have been delegated the appropriate permissions. In addition, you must run **wbadmin** from an elevated command prompt, by right-clicking **Command Prompt**, and then selecting **Run as administrator**.

Note

Windows Server Backup does not back up or recover registry user hives (HKEY\_CURRENT\_USER) as part of system state backup or system state recovery.

## Syntax

```
wbadmin delete systemstatebackup {-keepVersions:<numberofcopies> | -version:<versionidentifier> | -deleteoldest} [-backupTarget:<volumename>] [-machine:<backupmachinename>] [-quiet]
```

Important

You must only specify one of these parameters: **-keepVersions**, **-version**, or **-deleteOldest**.

### Parameters

| Parameter | Description |
| --- | --- |
| -keepVersions | Specifies the number of the latest system state backups to keep. The value must be a positive integer. The parameter value **-keepversions:0** deletes all the system state backups. |
| -version | Specifies the version identifier of the backup in MM/DD/YYYY-HH:MM format. If you don't know the version identifier, run the [wbadmin get versions](wbadmin-get-versions) command.<br>Versions made up of exclusively system state backups can be deleted using this command. Run the [wbadmin get items](wbadmin-get-items) command to view the version type. |
| -deleteOldest | Deletes the oldest system state backup. |
| -backupTarget | Specifies the storage location for the backup that you want to delete. The storage location for disk backups can be a drive letter, a mount point, or a GUID-based volume path. This value only needs to be specified for locating backups that are not on the local computer. Information about backups for the local computer is available in the backup catalog on the local computer. |
| -machine | Specifies the computer whose system state backup you want to delete. Useful when multiple computers were backed up to the same location. Should be used when the **-backupTarget** parameter is specified. |
| -quiet | Runs the command without prompts to the user. |

## Examples

To delete the system state backup created on March 31, 2013 at 10:00 AM, type:

```
wbadmin delete systemstatebackup -version:03/31/2013-10:00
```

To delete all system state backups, except the three most recent, type:

```
wbadmin delete systemstatebackup -keepVersions:3
```

To delete the oldest system state backup stored on disk f:, type:

```
wbadmin delete systemstatebackup -backupTarget:f:\ -deleteOldest
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wbadmin command](wbadmin)
- [wbadmin get versions command](wbadmin-get-versions)
- [wbadmin get items command](wbadmin-get-items)