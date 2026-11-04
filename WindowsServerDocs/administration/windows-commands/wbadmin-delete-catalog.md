---
layout: Conceptual
title: wbadmin delete catalog | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wbadmin-delete-catalog
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wbadmin delete catalog command, which deletes the backup catalog that is stored on the local computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 3ae88966-8ea3-898b-1282-504a6fc672fc
document_version_independent_id: fced70fb-ad37-8621-8911-524dd6faee3d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wbadmin-delete-catalog.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wbadmin-delete-catalog
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wbadmin-delete-catalog.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: d0d7e43c-c483-efbe-fcc5-c32a43024d20
---

# wbadmin delete catalog | Microsoft Learn

Deletes the backup catalog that is stored on the local computer. Use this command when the backup catalog has been corrupted and you can't restore it using the [wbadmin restore catalog](wbadmin-restore-catalog) command.

To delete a backup catalog using this command, you must be a member of the **Backup Operators** group or the **Administrators** group, or you must have been delegated the appropriate permissions. In addition, you must run **wbadmin** from an elevated command prompt, by right-clicking **Command Prompt**, and then selecting **Run as administrator**.

## Syntax

```
wbadmin delete catalog [-quiet]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -quiet | Runs the command without prompts to the user. |

#### Remarks

- If you delete the backup catalog of a computer, you'll no longer be able to get to any backups created for that computer using the Windows Server Backup snap-in. However, if you can get to another backup location and run the [wbadmin restore catalog](wbadmin-restore-catalog) command, you can restore the backup catalog from that location.
- We strongly recommend you create a new backup after you delete a backup catalog.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wbadmin command](wbadmin)
- [wbadmin restore catalog command](wbadmin-restore-catalog)
- [Remove-WBCatalog](/en-us/powershell/module/windowsserverbackup/Remove-WBCatalog)