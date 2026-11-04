---
layout: Conceptual
title: ftp open | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-open_1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp open command, which connects to the specified ftp server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 167b63ae-af49-3f92-917d-6c4f3321a3de
document_version_independent_id: 80937262-ea11-7f06-032e-0a5460dff54f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-open_1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-open_1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-open_1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9b2b9611-0b13-f429-92a0-0cda6d169e9a
---

# ftp open | Microsoft Learn

Connects to the specified ftp server.

## Syntax

```
open <computer> [<port>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<computer>` | Specifies the remote computer to which you are trying to connect. You can use an IP address or computer name (in which case a DNS server or Hosts file must be available). |
| `[<port>]` | Specifies a TCP port number to use to connect to an ftp server. By default, TCP port 21 is used. |

### Examples

To connect to the ftp server at *ftp.microsoft.com*, type:

```
open ftp.microsoft.com
```

To connect to the ftp server at *ftp.microsoft.com* that is listening on TCP port *755*, type:

```
open ftp.microsoft.com 755
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)