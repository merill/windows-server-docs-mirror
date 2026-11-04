---
layout: Conceptual
title: ftp mget | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-mget
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp mget command, which copies remote files to the local computer using the current file transfer type.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 128bcc45-fc7d-c767-9bf3-06bc1ae31d90
document_version_independent_id: 6ed034e9-b787-6a4d-4e98-f41eafe4727c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-mget.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-mget
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-mget.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4e317e46-bed4-0fd3-46e2-a35ca67ea084
---

# ftp mget | Microsoft Learn

Copies remote files to the local computer using the current file transfer type.

## Syntax

```
mget <remotefile>[ ]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<remotefile>` | Specifies the remote files to copy to the local computer. |

### Examples

To copy remote files *a.exe* and *b.exe* to the local computer using the current file transfer type, type:

```
mget a.exe b.exe
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ftp ascii command](ftp-ascii)
- [ftp binary command](ftp-binary)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)