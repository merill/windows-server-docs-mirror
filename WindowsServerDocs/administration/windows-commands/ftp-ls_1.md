---
layout: Conceptual
title: ftp ls | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-ls_1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp ls command, which displays an abbreviated list of files and subdirectories from the remote computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 09a2d52d-a875-83fd-427b-f4532b672b69
document_version_independent_id: 4a00f335-531a-d1e6-855f-86c3de393435
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-ls_1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-ls_1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-ls_1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4ab147cf-de53-3832-4351-7055a1dbb4de
---

# ftp ls | Microsoft Learn

Displays an abbreviated list of files and subdirectories from the remote computer.

## Syntax

```
ls [<remotedirectory>] [<localfile>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<remotedirectory>]` | Specifies the directory for which you want to see a listing. If no directory is specified, the current working directory on the remote computer is used. |
| `[<localfile>]` | Specifies a local file in which to store the listing. If a local file is not specified, results are displayed on the screen. |

### Examples

To display an abbreviated list of files and subdirectories from the remote computer, type:

```
ls
```

To get an abbreviated directory listing of *dir1* on the remote computer and save it in a local file called *dirlist.txt*, type:

```
ls dir1 dirlist.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)