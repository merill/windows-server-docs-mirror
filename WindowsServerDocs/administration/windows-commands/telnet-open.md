---
layout: Conceptual
title: telnet open | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/telnet-open
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the telnet open command, which connects to a telnet server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d8299f51-6913-e8e1-8421-791c179e90cc
document_version_independent_id: c188ec4b-e306-d3b6-2f24-13a99b49b9f9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/telnet-open.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/telnet-open
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/telnet-open.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ad6451f9-6ba1-7b01-9489-232028b744b2
---

# telnet open | Microsoft Learn

Connects to a telnet server.

## Syntax

```
o[pen] <hostname> [<port>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<hostname>` | Specifies the computer name or IP address. |
| `[<port>]` | Specifies the TCP port that the telnet server is listening on. The default is TCP port 23. |

## Examples

To connect to a telnet server at *telnet.microsoft.com*, type:

```
o telnet.microsoft.com
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)