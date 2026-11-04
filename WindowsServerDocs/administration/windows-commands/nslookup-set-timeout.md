---
layout: Conceptual
title: nslookup set timeout | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup-set-timeout
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nslookup set timeout command, which changes the initial number of seconds to wait for a reply to a lookup request.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c16b7395-b08e-1cdd-1c17-c502e96bc0f5
document_version_independent_id: b1f4227c-b27e-27c7-35f2-774d0b387ed2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nslookup-set-timeout.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nslookup-set-timeout
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nslookup-set-timeout.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6e5339f7-8ff0-0439-2f0c-e6769e68f1ad
---

# nslookup set timeout | Microsoft Learn

Changes the number of seconds to wait for a reply to a lookup request. Use the [nslookup set retry](nslookup-set-retry) command to determine the number of times to try to send the request.

## Syntax

```
set timeout=<number>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<number>` | Specifies the number of seconds to wait for a reply. The default number of seconds to wait is **2**. |
| /? | Displays help at the command prompt. |
| /help | Displays help at the command prompt. |

### Examples

To set the timeout for getting a response to 5 seconds:

```
set timeout=5
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [nslookup set retry](nslookup-set-retry)