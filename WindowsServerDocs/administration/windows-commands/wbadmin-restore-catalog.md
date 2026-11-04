---
layout: Conceptual
title: wbadmin restore catalog | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wbadmin-restore-catalog
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wbadmin restore catalog command, which recovers a backup catalog for the local computer from a storage location that you specify.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ac5d6f5c-9045-20c7-a3a7-59a95c9b0ea0
document_version_independent_id: ba7dd12d-6117-ad59-a541-714252e894d7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wbadmin-restore-catalog.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wbadmin-restore-catalog
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wbadmin-restore-catalog.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 1e5dcfb2-d295-091e-1a26-15ba82bb74bf
---

# wbadmin restore catalog | Microsoft Learn

Recovers a backup catalog for the local computer from a storage location that you specify.

To recover a backup catalog included in a specific backup using this command, you must be a member of the **Backup Operators** group or the **Administrators** group, or you must have been delegated the appropriate permissions. In addition, you must run **wbadmin** from an elevated command prompt, by right-clicking **Command Prompt**, and then selecting **Run as administrator**.

Note

If the location (disk, DVD, or remote shared folder) where you store your backups is damaged or lost and can't be used to restore the backup catalog, run the [wbadmin delete catalog](wbadmin-delete-catalog) command to delete the corrupted catalog. In this case, we recommend creating a new backup after your backup catalog is deleted.

## Syntax

```
wbadmin restore catalog -backupTarget:{<BackupDestinationVolume> | <NetworkShareHostingBackup>} [-machine:<BackupMachineName>] [-quiet]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -backupTarget | Specifies the location of the backup catalog of the system as it was at the point after the backup was created. |
| -machine | Specifies the name of the computer that you want to recover the backup catalog for. Use when backups for multiple computers have been stored at the same location. Should be used when **-backupTarget** is specified. |
| -quiet | Runs the command without prompts to the user. |

## Examples

To restore a catalog from a backup stored on disk D:, type:

```
wbadmin restore catalog -backupTarget:D
```

To restore a catalog from a backup stored in the shared folder `\\<servername>\<share>` of server01, type:

```
wbadmin restore catalog -backupTarget:\\servername\share -machine:server01
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wbadmin command](wbadmin)
- [wbadmin delete catalog command](wbadmin-delete-catalog)
- [Restore-WBCatalog](/en-us/powershell/module/windowsserverbackup/restore-wbcatalog)