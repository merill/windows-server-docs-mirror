---
layout: Conceptual
title: wbadmin start systemstaterecovery | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wbadmin-start-systemstaterecovery
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wbadmin start systemstaterecovery command, which performs a system state recovery to a location, and from a backup, that you specify.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 66ba4f0b-7b1c-be51-8fe3-2b7e6f1cd67f
document_version_independent_id: 5c47077f-defd-8524-e2ba-7f268bf164f3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wbadmin-start-systemstaterecovery.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wbadmin-start-systemstaterecovery
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wbadmin-start-systemstaterecovery.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: be60d53e-92a8-bf04-4cc7-318a5e10c22d
---

# wbadmin start systemstaterecovery | Microsoft Learn

Performs a system state recovery to a location and from a backup that you specify.

To perform a system state recovery using this command, you must be a member of the **Backup Operators** group or the **Administrators** group, or you must have been delegated the appropriate permissions. In addition, you must run **wbadmin** from an elevated command prompt, by right-clicking **Command Prompt**, and then selecting **Run as administrator**.

Note

Windows Server Backup doesn't back up or recover registry user hives (HKEY\_CURRENT\_USER) as part of system state backup or system state recovery.

## Syntax

```
wbadmin start systemstaterecovery -version:<VersionIdentifier> -showsummary [-backupTarget:{<BackupDestinationVolume> | <NetworkSharePath>}]
[-machine:<BackupMachineName>] [-recoveryTarget:<TargetPathForRecovery>] [-authsysvol] [-autoReboot] [-quiet]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -version | Specifies the version identifier of the backup to recover in MM/DD/YYYY-HH:MM format. If you don't know the version identifier, run the [wbadmin get versions command](wbadmin-get-versions). |
| -showsummary | Reports the summary of the last system state recovery (after the restart required to finish the operation). This parameter can't be accompanied by any other parameters. |
| -backupTarget | Specifies the storage location with the backup(s) you want to recover. This parameter is useful when the storage location is different from where backups are usually stored. |
| -machine | Specifies the name of the computer to recover the backup for. This parameter must be used when the **-backupTarget** parameter is specified. The **-machine** parameter is useful when multiple computers have been backed up to the same location. |
| -recoveryTarget | Specifies what directory to restore to. This parameter is useful if the backup is restored to an alternate location. |
| -authsysvol | Performs an authoritative restore of the System Volume (sysvol) shared directory. |
| -autoReboot | Specifies to restart the system at the end of the system state recovery operation. This parameter is valid only for a recovery to the original location. We don't recommend you use this parameter if you need to perform steps after the recovery operation. |
| -quiet | Runs the command without prompts to the user. |

## Examples

To start a system state recovery of the backup from 03/31/2020 at 9:00 A.M., type:

```
wbadmin start systemstaterecovery -version:03/31/2020-09:00
```

To start a system state recovery of the backup from 04/30/2020 at 9:00 A.M. that is stored on the shared resource `\\servername\share` for server01, type:

```
wbadmin start systemstaterecovery -version:04/30/2013-09:00 -backupTarget:\\servername\share -machine:server01
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wbadmin command](wbadmin)
- [Start-WBSystemStateRecovery](/en-us/powershell/module/windowsserverbackup/start-wbsystemstaterecovery)