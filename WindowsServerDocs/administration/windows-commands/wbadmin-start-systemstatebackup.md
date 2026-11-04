---
layout: Conceptual
title: wbadmin start systemstatebackup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wbadmin-start-systemstatebackup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wbadmin start systemstatebackup command, which creates a system state backup of the local computer and stores it on the location specified.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 60466bf4-2047-ba1d-d774-598755303ff7
document_version_independent_id: f9ebb8be-0956-955e-5d99-f03f78145de8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wbadmin-start-systemstatebackup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wbadmin-start-systemstatebackup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wbadmin-start-systemstatebackup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 56e44b8f-a8c7-4fcd-eada-e06e28fd0728
---

# wbadmin start systemstatebackup | Microsoft Learn

Creates a system state backup of the local computer and stores it on the location specified.

To perform a system state backup using this command, you must be a member of the **Backup Operators** group or the **Administrators** group, or you must have been delegated the appropriate permissions. In addition, you must run **wbadmin** from an elevated command prompt, by right-clicking **Command Prompt**, and then selecting **Run as administrator**.

Note

Windows Server Backup doesn't back up or recover registry user hives (HKEY\_CURRENT\_USER) as part of system state backup or system state recovery.

## Syntax

```
wbadmin start systemstatebackup -backupTarget:<VolumeName> [-quiet]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -backupTarget | Specifies the location where you want to store the backup. The storage location requires a drive letter or a GUID-based volume of the format: `\\?\Volume{*GUID*}`. Use the command `-backuptarget:\\servername\sharedfolder\` to store system state backups. |
| -quiet | Runs the command without prompts to the user. |

## Examples

To create a system state backup and store it on volume f, type:

```
wbadmin start systemstatebackup -backupTarget:f:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wbadmin command](wbadmin)
- [Start-WBBackup](/en-us/powershell/module/windowsserverbackup/start-wbbackup)