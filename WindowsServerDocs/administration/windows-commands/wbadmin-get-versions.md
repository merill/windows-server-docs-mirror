---
layout: Conceptual
title: wbadmin get versions | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wbadmin-get-versions
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wbadmin get versions command, which lists details about the available backups that are stored on the local computer or another computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d8ad1a9a-a881-1aa0-1915-bfc52c32d928
document_version_independent_id: dfc0b36b-835b-b952-eea5-b41ab9ab88fd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wbadmin-get-versions.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wbadmin-get-versions
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wbadmin-get-versions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 6fa05621-b892-ae5c-403c-3c526f825ee0
---

# wbadmin get versions | Microsoft Learn

Lists details about the available backups that are stored on the local computer or another computer. The details provided for a backup include the backup time, the backup storage location, the version identifier, and the type of recoveries you can perform.

To get details about available backups using this command, you must be a member of the **Backup Operators** group or the **Administrators** group, or you must have been delegated the appropriate permissions. In addition, you must run **wbadmin** from an elevated command prompt, by right-clicking **Command Prompt**, and then selecting **Run as administrator**.

If this command is used without parameters, it lists all backups of the local computer, even if those backups are not available.

## Syntax

```
wbadmin get versions [-backupTarget:{<BackupTargetLocation> | <NetworkSharePath>}] [-machine:BackupMachineName]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -backupTarget | Specifies the storage location that contains the backups that you want the details for. Use for listing backups stored at that target location. Backup target locations can be locally attached disk drives, volumes, remote shared folders, removable media such as DVD drives or other optical media. If this command is run on the same computer where the backup was created, this parameter isn't needed. However, this parameter is required to get information about a backup created from another computer. |
| -machine | Specifies the computer that you want backup details for. Use when backups of multiple computers are stored in the same location. Should be used when **-backupTarget** is specified. |

## Examples

To see a list of available backups that are stored on volume H:, type:

```
wbadmin get versions -backupTarget:H:
```

To see a list of available backups that are stored in the remote shared folder `\\<servername>\<share>` for the computer server01, type:

```
wbadmin get versions -backupTarget:\\servername\share -machine:server01
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wbadmin command](wbadmin)
- [wbadmin get items command](wbadmin-get-items)
- [Get-WBBackupTarget](/en-us/powershell/module/windowsserverbackup/get-wbbackuptarget)