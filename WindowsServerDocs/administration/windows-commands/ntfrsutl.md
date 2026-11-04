---
layout: Conceptual
title: ntfrsutl | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ntfrsutl
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ntfrsutl command, which dumps the internal tables, thread, and memory information for the NT File Replication Service (NTFRS).
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 56613a85-8a18-e6e6-c7e5-2f9c5aa6c9cf
document_version_independent_id: ff6d210a-d659-21aa-34f1-0d40921d700a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ntfrsutl.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ntfrsutl
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ntfrsutl.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6b352bb8-21bf-9a42-4af6-9728717f2b1b
---

# ntfrsutl | Microsoft Learn

Dumps the internal tables, thread, and memory information for the NT File Replication Service (NTFRS) from both the local and remote servers. The recovery setting for NTFRS in Service Control Manager (SCM) can be critical to locating and keeping important log events on the computer. This tool provides a convenient method of reviewing those settings.

## Syntax

```
ntfrsutl[idtable|configtable|inlog|outlog][<computer>]
ntfrsutl[memory|threads|stage][<computer>]
ntfrsutl ds[<computer>]
ntfrsutl [sets][<computer>]
ntfrsutl [version][<computer>]
ntfrsutl poll[/quickly[=[<n>]]][/slowly[=[<n>]]][/now][<computer>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| idtable | Specifies the ID table. |
| configtable | Specifies the FRS configuration table. |
| inlog | Specifies the inbound log. |
| outlog | Specifies the outbound log. |
| `<computer>` | Specifies the computer. |
| memory | Specifies the memory usage. |
| threads | Specifies the memory usage. |
| stage | Specifies the memory usage. |
| ds | Lists the NTFRS service's view of the DS. |
| sets | Specifies the active replica sets. |
| version | Specifies the API and NTFRS service versions. |
| poll | Specifies the current polling intervals.<br>- `/quickly` - Polls quickly until it retrieves a stable configuration.<br>- `/quickly=` - Polls quickly every default number of minutes.<br>- `/quickly=<n>` - Polls quickly every *n* minutes.<br>- `/slowly` - Polls slowly until it retrieves a stable configuration.<br>- `/slowly=` - Polls slowly every default number of minutes.<br>- `/slowly=<n>` - Polls slowly every *n* minutes.<br>- `/now` - Polls now. |
| /? | Displays help at the command prompt. |

### Examples

To determine the polling interval for file replication, type:

```
C:\Program Files\SupportTools>ntfrsutl poll wrkstn-1
```

To determine the current NTFRS application program interface (API) version, type:

```
C:\Program Files\SupportTools>ntfrsutl version
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)