---
layout: Conceptual
title: ftp dir | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-dir
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp dir command, which displays a list of directory files and subdirectories on a remote computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 839cfd13-4205-c6d1-605d-edbed19c884a
document_version_independent_id: 54d1e855-7a87-048a-ff87-fdada5790f5e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-dir.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-dir
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-dir.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9219da3c-7d5e-232f-50bc-dafa1d726479
---

# ftp dir | Microsoft Learn

Displays a list of directory files and subdirectories on a remote computer.

## Syntax

```
dir [<remotedirectory>] [<localfile>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<remotedirectory>]` | Specifies the directory for which you want to see a listing. If no directory is specified, the current working directory on the remote computer is used. |
| `[<localfile>]` | Specifies a local file in which to store the directory listing. If a local file is not specified, results are displayed on the screen. |

### Examples

To display a directory listing for *dir1* on the remote computer, type:

```
dir dir1
```

To save a list of the current directory on the remote computer in the local file *dirlist.txt*, type:

```
dir . dirlist.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)