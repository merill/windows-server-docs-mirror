---
layout: Conceptual
title: auditpol | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/auditpol
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the auditpol command, which displays information about and performs functions to manipulate audit policies.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b4440e46-2554-5e3f-07fa-647bf9685768
document_version_independent_id: 21da15dd-cfd9-cde8-47af-83efedac2265
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/auditpol.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/auditpol
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/auditpol.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 06dbff49-6529-6b33-00c8-4aa059ab8361
---

# auditpol | Microsoft Learn

Displays information about and performs functions to manipulate audit policies, including:

- Setting and querying a system audit policy.
- Setting and querying a per-user audit policy.
- Setting and querying auditing options.
- Setting and querying the security descriptor used to delegate access to an audit policy.
- Reporting or backing up an audit policy to a comma-separated value (CSV) text file.
- Loading an audit policy from a CSV text file.
- Configuring global resource SACLs.

## Syntax

```
auditpol command [<sub-command><options>]
```

### Parameters

| Sub-command | Description |
| --- | --- |
| /get | Displays the current audit policy. For more information, see [auditpol get](auditpol-get) for syntax and options. |
| /set | Sets the audit policy. For more information, see [auditpol set](auditpol-set) for syntax and options. |
| /list | Displays selectable policy elements. For more information, see [auditpol list](auditpol-list) for syntax and options. |
| /backup | Saves the audit policy to a file. For more information, see [auditpol backup](auditpol-backup) for syntax and options. |
| /restore | Restores the audit policy from a file that was previously created by using auditpol /backup. For more information, see [auditpol restore](auditpol-restore) for syntax and options. |
| /clear | Clears the audit policy. For more information, see [auditpol clear](auditpol-clear) for syntax and options. |
| /remove | Removes all per-user audit policy settings and disables all system audit policy settings. For more information, see [auditpol remove](auditpol-remove) for syntax and options. |
| /resourceSACL | Configures global resource system access control lists (SACLs). **Note:** Applies only to Windows 7 and Windows Server 2008 R2. For more information, see [auditpol resourceSACL](auditpol-resourcesacl). |
| /? | Displays help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)