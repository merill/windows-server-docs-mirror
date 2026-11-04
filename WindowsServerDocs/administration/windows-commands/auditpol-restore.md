---
layout: Conceptual
title: auditpol restore | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/auditpol-restore
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the auditpol restore command, which restores system audit policy settings, per-user audit policy settings for all users, and all auditing options from a file that is syntactically consistent with the comma-separated value (CSV) file format used by the /backup option.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: bf1b3681-0fc2-dad7-058e-634681babfc5
document_version_independent_id: f58eb7e5-76ac-d7d3-43cf-29493e616e5b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/auditpol-restore.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/auditpol-restore
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/auditpol-restore.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a3433c60-c330-6a1c-9384-3c045d6559da
---

# auditpol restore | Microsoft Learn

Restores system audit policy settings, per-user audit policy settings for all users, and all auditing options from a file that is syntactically consistent with the comma-separated value (CSV) file format used by the /backup option.

To perform *restore* operations on the *per-user* and *system* policies, you must have **Write** or **Full Control** permission for that object set in the security descriptor. You can also perform *restore* operations if you have the **Manage auditing and security log** (SeSecurityPrivilege) user right, which is useful when restoring the security descriptor in the event of an error or malicious attack.

## Syntax

```
auditpol /restore /file:<filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| /file | Specifies the file from which the audit policy should be restored. The file must have been created by using the /backup option or must be syntactically consistent with the CSV file format used by the /backup option. |
| /? | Displays help at the command prompt. |

## Examples

To restore system audit policy settings, per-user audit policy settings for all users, and all auditing options from a file named auditpolicy.csv that was created by using the /backup command, type:

```
auditpol /restore /file:c:\auditpolicy.csv
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [auditpol backup](auditpol-backup)
- [auditpol commands](auditpol)