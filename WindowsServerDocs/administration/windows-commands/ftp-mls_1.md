---
layout: Conceptual
title: ftp mls | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-mls_1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp mls command, which displays an abbreviated list of files and subdirectories in a remote directory.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 56af115e-ff19-f4d2-b145-eac3b1399a81
document_version_independent_id: b1adad75-17b2-23e5-a941-9dc2d42aaa0f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-mls_1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-mls_1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-mls_1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0eccb7c5-fd4c-4923-8673-f3f40a858a36
---

# ftp mls | Microsoft Learn

Displays an abbreviated list of files and subdirectories in a remote directory.

## Syntax

```
mls <remotefile>[ ] <localfile>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<remotefile>` | Specifies the file for which you want to see a listing. When specifying *remotefiles*, use a hyphen to represent the current working directory on the remote computer. |
| `<localfile>` | Specifies a local file in which to store the listing. When specifying *localfile*, use a hyphen to display the listing on the screen. |

### Examples

To display an abbreviated list of files and subdirectories for *dir1* and *dir2*, type:

```
mls dir1 dir2 -
```

To save an abbreviated list of files and subdirectories for *dir1* and *dir2* in the local file *dirlist.txt*, type:

```
mls dir1 dir2 dirlist.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)