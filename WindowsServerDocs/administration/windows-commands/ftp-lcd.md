---
layout: Conceptual
title: ftp lcd | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-lcd
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp lcd command, which changes the working directory on the local computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: aa5908ab-c5c2-af5c-5e9f-efc447168186
document_version_independent_id: 8bb558bc-caf2-27c5-cce4-0f5dd2eed06c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-lcd.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-lcd
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-lcd.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9cd1a566-007c-caee-de63-980a0fb9f3df
---

# ftp lcd | Microsoft Learn

Changes the working directory on the local computer. By default, the working directory is the directory in which the **ftp** command was started.

## Syntax

```
lcd [<directory>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<directory>]` | Specifies the directory on the local computer to which to change. If *directory* isn't specified, the current working directory is changed to the default directory. |

### Examples

To change the working directory on the local computer to *c:\dir1*, type:

```
lcd c:\dir1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)