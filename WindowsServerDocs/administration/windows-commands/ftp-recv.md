---
layout: Conceptual
title: ftp recv | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-recv
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp recv command, which copies a remote file to the local computer using the current file transfer type.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 45184806-355a-2f56-6b20-4ab3b3df733d
document_version_independent_id: 108eb0eb-4a00-56e8-509f-48a7c446acfd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-recv.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-recv
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-recv.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d001993d-db86-74f2-cc96-6633fbd63b79
---

# ftp recv | Microsoft Learn

Copies a remote file to the local computer using the current file transfer type.

Note

This command is the same as the [ftp get command](ftp-get).

## Syntax

```
recv <remotefile> [<localfile>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<remotefile>` | Specifies the remote file to copy. |
| `[<localfile>]` | Specifies the name of the file to use on the local computer. If *localfile* isn't specified, the file is given the name of the *remotefile*. |

### Examples

To copy *test.txt* to the local computer using the current file transfer, type:

```
recv test.txt
```

To copy *test.txt* to the local computer as *test1.txt* using the current file transfer, type:

```
recv test.txt test1.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ftp get command](ftp-get)
- [ftp ascii command](ftp-ascii)
- [ftp binary command](ftp-binary)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)