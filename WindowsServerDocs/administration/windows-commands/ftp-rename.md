---
layout: Conceptual
title: ftp rename | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-rename
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp rename command, which renames remote files.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 8c286e68-9c20-3aa3-e8a7-43f6d9a88685
document_version_independent_id: b9a33b16-5b65-72b1-144b-ea6d78024a58
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-rename.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-rename
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-rename.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a14b3651-49b2-94c5-d8d8-281d109f8073
---

# ftp rename | Microsoft Learn

Renames remote files.

## Syntax

```
rename <filename> <newfilename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<filename>` | Specifies the file that you want to rename. |
| `<newfilename>` | Specifies the new file name. |

### Examples

To rename the remote file *example.txt* to *example1.txt*, type:

```
rename example.txt example1.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)