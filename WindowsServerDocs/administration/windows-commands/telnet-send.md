---
layout: Conceptual
title: telnet send | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/telnet-send
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the telnet send command, which sends telnet commands to the telnet server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b59a0198-0d2c-8035-73f4-91dcab658369
document_version_independent_id: 2beaa84f-fde4-11ae-d283-3a5cc67c8709
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/telnet-send.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/telnet-send
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/telnet-send.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 90ec2c37-c749-1abc-0b0b-bd241173ffc4
---

# telnet send | Microsoft Learn

Sends telnet commands to the telnet server.

## Syntax

```
sen {ao | ayt | brk | esc | ip | synch | <string>} [?]
```

### Parameters

| Parameter | Description |
| --- | --- |
| ao | Sends the telnet command **Abort Output**. |
| ayt | Sends the telnet command **Are You There?** |
| brk | Sends the telnet command **brk**. |
| esc | Sends the current telnet escape character. |
| ip | Sends the telnet command **Interrupt Process**. |
| synch | Sends the telnet command synch. |
| `<string>` | Sends whatever string you type to the telnet server. |
| ? | Displays help associated with this command. |

## Example

To send the **Are you there?** command to the telnet server, type:

```
sen ayt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)