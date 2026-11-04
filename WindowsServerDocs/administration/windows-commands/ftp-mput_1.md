---
layout: Conceptual
title: ftp mput | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-mput_1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp mput command, which copies local files to the remote computer using the current file transfer type.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9f382662-0c03-9040-c1ae-e5ce3150a33a
document_version_independent_id: 221ae978-89e7-7256-2274-1882d0fc9f5f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-mput_1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-mput_1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-mput_1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5e49ed33-0477-c5a2-49e2-e14c1a0dae3b
---

# ftp mput | Microsoft Learn

Copies local files to the remote computer using the current file transfer type.

## Syntax

```
mput <localfile>[ ]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<localfile>` | Specifies the local file to copy to the remote computer. |

### Examples

To copy *Program1.exe* and *Program2.exe* to the remote computer using the current file transfer type, type:

```
mput Program1.exe Program2.exe
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ftp ascii command](ftp-ascii)
- [ftp binary command](ftp-binary)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)