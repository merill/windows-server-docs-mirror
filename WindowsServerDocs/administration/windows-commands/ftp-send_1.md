---
layout: Conceptual
title: ftp send | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-send_1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp send command, which copies a local file to the remote computer using the current file transfer type.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ccfd3104-f1b1-5e53-79ff-89f05ff88956
document_version_independent_id: a47f9e7e-5a91-9db0-624a-b2a9cff9a138
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-send_1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-send_1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-send_1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 47e64c62-b38b-2f18-c031-5c9bba8e377c
---

# ftp send | Microsoft Learn

Copies a local file to the remote computer using the current file transfer type.

Note

This command is the same as the [ftp put command](ftp-put).

## Syntax

```
send <localfile> [<remotefile>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<localfile>` | Specifies the local file to copy. |
| `<remotefile>` | Specifies the name to use on the remote computer. If you don't specify a *remotefile*, the file will get the *localfile* name. |

### Examples

To copy the local file *test.txt* and name it *test1.txt* on the remote computer, type:

```
send test.txt test1.txt
```

To copy the local file *program.exe* to the remote computer, type:

```
send program.exe
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)