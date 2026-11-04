---
layout: Conceptual
title: wbadmin get items | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wbadmin-get-items
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wbadmin get items command, which lists the items included in a specific backup.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e331eaba-58c0-cf70-2ec3-9439cbb7973c
document_version_independent_id: 095da831-5a54-70d7-d662-2ac0b358cf84
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wbadmin-get-items.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wbadmin-get-items
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wbadmin-get-items.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: e017616f-4141-c0c9-0df6-beae62aac6a8
---

# wbadmin get items | Microsoft Learn

Lists the items included in a specific backup.

To list the items included in a specific backup using this command, you must be a member of the **Backup Operators** group or the **Administrators** group, or you must have been delegated the appropriate permissions. In addition, you must run **wbadmin** from an elevated command prompt, by right-clicking **Command Prompt**, and then selecting **Run as administrator**.

## Syntax

```
wbadmin get items -version:<VersionIdentifier> [-backupTarget:{<BackupDestinationVolume> | <NetworkSharePath>}] [-machine:<BackupMachineName>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -version | Specifies the version of the backup in MM/DD/YYYY-HH:MM format. If you don't know the version information, run the [wbadmin get versions](wbadmin-get-versions) command. |
| -backupTarget | Specifies the storage location that contains the backups for which you want the details. Use for listing backups stored at that target location. Backup target locations can be a locally attached disk drive or a remote shared folder. If this command is run on the same computer where the backup was created, this parameter isn't needed. However, this parameter is required to get information about a backup created from another computer. |
| -machine | Specifies the name of the computer that you want the backup details for. Useful when multiple computers have been backed up to the same location. Should be used when **-backupTarget** is specified. |

## Examples

To list items from the backup that was run on March 31, 2013 at 9:00 A.M., type:

```
wbadmin get items -version:03/31/2013-09:00
```

To list items from the backup of server01 that was run on April 30, 2013 at 9:00 A.M. and stored on `\\<servername>\<share>`, type:

```
wbadmin get items -version:04/30/2013-09:00 -backupTarget:\\servername\share -machine:server01
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wbadmin command](wbadmin)
- [wbadmin get versions command](wbadmin-get-versions)
- [Get-WBBackupSet](/en-us/powershell/module/windowsserverbackup/get-wbbackupset)