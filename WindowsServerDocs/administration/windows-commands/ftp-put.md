---
layout: Conceptual
title: ftp put | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-put
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp put command, which copies a local file to the remote computer using the current file transfer type.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-03-30T00:00:00.0000000Z
locale: en-us
document_id: 96757e07-4741-6375-3ced-0dce0713120b
document_version_independent_id: 2b85a083-f842-6fbf-ca94-0ae010cbb033
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-put.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-put
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-put.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0b2a4ce8-cf41-e223-5a5c-e7e39b6cf3da
---

# ftp put | Microsoft Learn

Copies a local file to the remote computer using the current file transfer type.

Note

This command is the same as the [ftp send command](ftp-send_1).

## Syntax

```
put <localfile> [<remotefile>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<localfile>` | Specifies the local file to copy. |
| `[<remotefile>]` | Specifies the name to use on the remote computer. If you don't specify a *remotefile*, the file is give the *localfile* name. |

### Examples

To copy the local file *test.txt* and name it *test1.txt* on the remote computer, type:

```
put test.txt test1.txt
```

To copy the local file *program.exe* to the remote computer, type:

```
put program.exe
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ftp ascii command](ftp-ascii)
- [ftp binary command](ftp-binary)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)