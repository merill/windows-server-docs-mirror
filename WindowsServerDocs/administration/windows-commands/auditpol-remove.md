---
layout: Conceptual
title: auditpol remove | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/auditpol-remove
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the auditpol remove command; auditpol removes the per-user audit policy for a specified account or all accounts.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2023-04-01T00:00:00.0000000Z
locale: en-us
document_id: 37980173-f598-6bc4-9f5a-361c31d5b777
document_version_independent_id: 3a3b667f-46c7-0b7b-5f5c-50a4e7dee908
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/auditpol-remove.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/auditpol-remove
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/auditpol-remove.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d57a3af7-4d17-13fb-776b-b8cebc941c3f
---

# auditpol remove | Microsoft Learn

Applies to: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

The auditpol remove command removes the per-user audit policy for a specified account or all accounts.

To perform *remove* operations on the *per-user* policy, you must have **Write** or **Full Control** permissions for that object set in the security descriptor. You can also perform *remove* operations if you have the **Manage auditing and security log** (`SeSecurityPrivilege`) user right. However, this right allows access that isn't necessary to perform the overall *remove* operations.

## Syntax

```
auditpol /remove [/user[:<username>|<{SID}>]]
[/allusers]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /user | Specifies the security identifier (SID) or user name for the user for whom the per-user audit policy is to be deleted. |
| /allusers | Removes the per-user audit policy for all users. |
| /? | Displays help at the command prompt. |

## Examples

To remove the per-user audit policy for user `mikedan` by name, type:

```
auditpol /remove /user:mikedan
```

To remove the per-user audit policy for user `mikedan` by SID, type:

```
auditpol /remove /user:{S-1-5-21-397123471-12346959}
```

To remove the per-user audit policy for all users, type:

```
auditpol /remove /allusers
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [auditpol commands](auditpol)