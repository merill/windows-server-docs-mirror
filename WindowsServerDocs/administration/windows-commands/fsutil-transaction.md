---
layout: Conceptual
title: fsutil transaction | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-transaction
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil transaction command, which manages NTFS transactions.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: cfcc3587-2d8e-5edb-ada1-33be38896dcd
document_version_independent_id: ae53ae54-cf40-b715-8924-15b0a3c4b277
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-transaction.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-transaction
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-transaction.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7a95aa32-8589-3795-efac-7c7b3d0e5f82
---

# fsutil transaction | Microsoft Learn

Manages NTFS transactions.

## Syntax

```
fsutil transaction [commit] <GUID>
fsutil transaction [fileinfo] <filename>
fsutil transaction [list]
fsutil transaction [query] [{files | all}] <GUID>
fsutil transaction [rollback] <GUID>
```

### Parameters

| Parameter | Description |
| --- | --- |
| commit | Marks the end of a successful implicit or explicit specified transaction. |
| `<GUID>` | Specifies the GUID value that represents a transaction. |
| fileinfo | Displays transaction information for the specified file. |
| `<filename>` | Specifies full path and file name. |
| list | Displays a list of currently running transactions. |
| query | Displays information for the specified transaction.<br>- If `fsutil transaction query files` is specified, the file information is displayed only for the specified transaction.<br>- If `fsutil transaction query all` is specified, all information for the transaction will be displayed. |
| rollback | Rolls back a specified transaction to the beginning. |

### Examples

To display transaction information for file *c:\test.txt*, type:

```
fsutil transaction fileinfo c:\test.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)
- [Transactional NTFS](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc730726%28v=ws.10%29)