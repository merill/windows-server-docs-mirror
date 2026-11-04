---
layout: Conceptual
title: auditpol list | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/auditpol-list
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the auditpol list command, which lists audit policy categories and subcategories, or lists users for whom a per-user audit policy is defined.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ea90db76-5b81-6a4a-7d5f-eefc6e7ced28
document_version_independent_id: eb25d46c-5156-88f2-d569-f660982e5a87
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/auditpol-list.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/auditpol-list
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/auditpol-list.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7badbdff-072d-0a66-5ddc-13a965d88142
---

# auditpol list | Microsoft Learn

Lists audit policy categories and subcategories, or lists users for whom a per-user audit policy is defined.

To perform *list* operations on the *per-user* policy, you must have **Read** permission for that object set in the security descriptor. You can also perform *list* operations if you have the **Manage auditing and security log** (SeSecurityPrivilege) user right. However, this right allows additional access that is not necessary to perform the overall *list* operations.

## Syntax

```
auditpol /list
[/user|/category|subcategory[:<categoryname>|<{guid}>|*]]
[/v] [/r]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /user | Retrieves all users for whom the per-user audit policy has been defined. If used with the /v parameter, the security identifier (SID) of the user is also displayed. |
| /category | Displays the names of categories understood by the system. If used with the /v parameter, the category globally unique identifier (GUID) is also displayed. |
| /subcategory | Displays the names of subcategories and their associated GUID. |
| /v | Displays the GUID with the category or subcategory, or when used with /user, displays the SID of each user. |
| /r | Displays the output as a report in comma-separated value (CSV) format. |
| /? | Displays help at the command prompt. |

## Examples

To list all users who have a defined audit policy, type:

```
auditpol /list /user
```

To list all users who have a defined audit policy and their associated SID, type:

```
auditpol /list /user /v
```

To list all categories and subcategories in report format, type:

```
auditpol /list /subcategory:* /r
```

To list the subcategories of the detailed Tracking and DS Access categories, type:

```
auditpol /list /subcategory:detailed Tracking,DS Access
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [auditpol commands](auditpol)