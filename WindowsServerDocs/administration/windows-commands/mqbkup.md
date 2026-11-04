---
layout: Conceptual
title: mqbkup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/mqbkup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the mqbkup command, which backs up MSMQ message files and registry settings to a storage device and restores previously-stored messages and settings.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a389db13-8055-dbb2-1754-c73e08a6aa42
document_version_independent_id: 9f08bf7e-5987-a2d2-32e3-9f2b46fecdd1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/mqbkup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/mqbkup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/mqbkup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d2d68209-524d-023f-22a5-ae63d33a6b33
---

# mqbkup | Microsoft Learn

Backs up MSMQ message files and registry settings to a storage device and restores previously-stored messages and settings.

Both the backup and the restore operations stop the local MSMQ service. If the MSMQ service was started beforehand, the utility will attempt to restart the MSMQ service at the end of the backup or the restore operation. If the service was already stopped before running the utility, no attempt to restart the service is made.

Before using the MSMQ Message Backup/Restore utility you must close all local applications that are using MSMQ.

## Syntax

```
mqbkup {/b | /r} <folder path_to_storage_device>
```

### Parameters

| Parameter | Description |
| --- | --- |
| /b | Specifies backup operation. |
| /r | Specifies restore operation. |
| `<folder path_to_storage_device>` | Specifies the path where the MSMQ message files and registry settings are stored. |
| /? | Displays help at the command prompt. |

#### Remarks

- If a specified folder doesn't exist while performing either the backup or restore operation, the folder is automatically created by the utility.
- If you choose to specify an existing folder, it must be empty. If you specify a non-empty folder, the utility deletes every file and subfolder contained within it. In this case, you'll be prompted to give permission to delete existing files and subfolders. You can use the **/y** parameter to indicate that you agree beforehand to the deletion of all existing files and subfolders in the specified folder.
- The locations of folders used to store MSMQ message files are stored in the registry. Therefore, the utility restores MSMQ message files to the folders specified in the registry and not to the storage folders used before the restore operation.

### Examples

To backup all MSMQ message files and registry settings, and to store them in the *msmqbkup* folder on your C: drive, type:

```
mqbkup /b c:\msmqbkup
```

To delete all existing files and subfolders in the *oldbkup* folder on your C: drive, and then to store MSMQ message files and registry settings in the folder, type:

```
mqbkup /b /y c:\oldbkup
```

To restore MSMQ messages and registry settings, type:

```
mqbkup /r c:\msmqbkup
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [MSMQ Powershell Reference](/en-us/powershell/module/msmq/)