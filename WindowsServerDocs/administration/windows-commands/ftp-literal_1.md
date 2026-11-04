---
layout: Conceptual
title: ftp literal | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-literal_1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp literal command, which sends verbatim arguments to the remote ftp server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 47dd630f-7bdc-0c56-8b56-9373060d5e0c
document_version_independent_id: 51696bd0-6b9f-e5d0-1d42-c2b09b974192
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-literal_1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-literal_1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-literal_1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ddff19fd-349f-c51c-a627-c31b9cc7130f
---

# ftp literal | Microsoft Learn

Sends verbatim arguments to the remote ftp server. A single ftp reply code is returned.

Note

This command is the same as the [ftp quote command](ftp-quote).

## Syntax

```
literal <argument> [ ]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<argument>` | Specifies the argument to send to the ftp server. |

### Examples

To send a **quit** command to the remote ftp server, type:

```
literal quit
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ftp quote command](ftp-quote)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)