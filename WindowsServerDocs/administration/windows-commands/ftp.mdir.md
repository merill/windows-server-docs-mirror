---
layout: Conceptual
title: ftp mdir | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp.mdir
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp mdir command, which displays a directory list of files and subdirectories in a remote directory.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ede79591-6b4c-ad5e-f279-d19010287bd7
document_version_independent_id: 47c883b7-97be-c727-86df-e81a1c2365f5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp.mdir.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp.mdir
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp.mdir.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6335b009-3153-004a-a09e-ded21952d985
---

# ftp mdir | Microsoft Learn

Displays a directory list of files and subdirectories in a remote directory.

## Syntax

```
mdir <remotefile>[...] <localfile>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<remotefile>` | Specifies the directory or file for which you want to see a listing. You can specify multiple *remotefiles*. Type a hyphen (-) to use the current working directory on the remote computer. |
| `<localfile>` | Specifies a local file to store the listing. This parameter is required. Type a hyphen (-) to display the listing on the screen. |

### Examples

To display a directory listing of *dir1* and *dir2* on the screen, type:

```
mdir dir1 dir2 -
```

To save the combined directory listing of *dir1* and *dir2* in a local file called *dirlist.txt*, type:

```
mdir dir1 dir2 dirlist.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)