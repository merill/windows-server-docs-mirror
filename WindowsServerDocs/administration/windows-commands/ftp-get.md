---
layout: Conceptual
title: ftp get | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-get
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp get command, which copies a remote file to the local computer using the current file transfer type.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 14889afe-2fef-e81b-40ff-d6f9cffaedc7
document_version_independent_id: 950226aa-699d-29ce-bbd4-15c0f7cbe5b4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-get.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-get
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-get.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 79971dce-802b-142f-1b99-f2b5a9ec5ed5
---

# ftp get | Microsoft Learn

Copies a remote file to the local computer using the current file transfer type.

Note

This command is the same as the [ftp recv command](ftp-recv).

## Syntax

```
get <remotefile> [<localfile>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<remotefile>` | Specifies the remote file to copy. |
| `[<localfile>]` | Specifies the name of the file to use on the local computer. If *localfile* isn't specified, the file is given the name of the *remotefile*. |

### Examples

To copy *test.txt* to the local computer using the current file transfer, type:

```
get test.txt
```

To copy *test.txt* to the local computer as *test1.txt* using the current file transfer, type:

```
get test.txt test1.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ftp recv command](ftp-recv)
- [ftp ascii command](ftp-ascii)
- [ftp binary command](ftp-binary)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)