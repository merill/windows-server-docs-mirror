---
layout: Conceptual
title: auditpol backup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/auditpol-backup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the auditpol backup command that backs up system audit policy settings, per-user audit policy settings for all users, and all auditing options to a comma-separated value (CSV) text file.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2023-04-01T00:00:00.0000000Z
locale: en-us
document_id: 04c4c8a7-b2bd-639b-aff6-7227fc49ddb2
document_version_independent_id: e72be117-9dd9-9ec2-af6f-6585ebb95f72
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/auditpol-backup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/auditpol-backup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/auditpol-backup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1def86c6-6b73-3f97-15a6-2f3a3aa0ab21
---

# auditpol backup | Microsoft Learn

Applies to: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

The auditpol backup command backs up system audit policy settings, per-user audit policy settings for all users, and all auditing options to a comma-separated value (CSV) text file.

To perform *backup* operations on the *per-user* and *system* policies, you need **Write** or **Full Control** permissions for that object set in the security descriptor. You can also perform *backup* operations if you have the **Manage auditing and security log** (SeSecurityPrivilege) user right. However, this right allows access that isn't necessary to perform the overall *backup* operations.

## Syntax

```
auditpol /backup /file:<filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| /file | Specifies the file name of the for the back up. |
| /? | Displays help at the command prompt. |

## Examples

You can back up the following settings to a CSV-formatted text file:

- Per-user audit policy settings for all users
- System audit policy settings
- All auditing options

To back up these settings to a file named auditpolicy.csv, type the following command:

```
auditpol /backup /file:C:\auditpolicy.csv
```

Note

If no drive is specified, the current directory is used.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [auditpol restore](auditpol-restore)
- [auditpol commands](auditpol)