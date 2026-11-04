---
layout: Conceptual
title: auditpol clear | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/auditpol-clear
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the auditpol clear command, which deletes the per-user audit policy for all users, resets (disables) the system audit policy for all subcategories, and sets all the auditing options to disabled.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ae84e989-fa04-726b-0028-7e8529a06c8e
document_version_independent_id: 3ca3ecf5-a7cf-9d13-f38e-df9c2cd5aa4f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/auditpol-clear.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/auditpol-clear
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/auditpol-clear.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a3775554-82ae-fb64-e93d-263d2f271561
---

# auditpol clear | Microsoft Learn

Deletes the per-user audit policy for all users, resets (disables) the system audit policy for all subcategories, and sets all the auditing options to disabled.

To perform *clear* operations on the *per-user* and *system* policies, you must have **Write** or **Full Control** permission for that object set in the security descriptor. You can also perform *clear* operations if you have the **Manage auditing and security log** (SeSecurityPrivilege) user right. However, this right allows additional access that is not necessary to perform the overall *clear* operations.

## Syntax

```
auditpol /clear [/y]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /y | Suppresses the prompt to confirm if all audit policy settings should be cleared. |
| /? | Displays help at the command prompt. |

## Examples

To delete the per-user audit policy for all users, reset (disable) the system audit policy for all subcategories, and set all the audit policy settings to disabled, at a confirmation prompt, type:

```
auditpol /clear
```

To delete the per-user audit policy for all users, reset the system audit policy settings for all subcategories, and set all the audit policy settings to disabled, without a confirmation prompt, type:

```
auditpol /clear /y
```

Note

The preceding example is useful when using a script to perform this operation.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [auditpol commands](auditpol)