---
layout: Conceptual
title: ftp append | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-append
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp append command, which appends a local file to a file on the remote computer using the current file type setting.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 5033f956-184d-1324-9f5e-809777ff1f9d
document_version_independent_id: 9255c08a-4569-cba8-ed55-6a6ea6e03042
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-append.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-append
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-append.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 657139fc-d7b4-971b-6a05-6473d46ae087
---

# ftp append | Microsoft Learn

Appends a local file to a file on the remote computer using the current file type setting.

## Syntax

```
append <localfile> [remotefile]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<localfile>` | Specifies the local file to add. |
| [remotefile] | Specifies the file on the remote computer to which `<localfile>` is added. If you don't use this parameter, the `<localfile>` name is used in place of the remote file name. |

### Examples

To append *file1.txt* to *file2.txt* on the remote computer, type:

```
append file1.txt file2.txt
```

To append the local *file1.txt* to a file named *file1.txt* on the remote computer.

```
append file1.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)