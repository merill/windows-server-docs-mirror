---
layout: Conceptual
title: bitsadmin cache and setexpirationtime | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-cache-and-setexpirationtime
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin cache and setexpirationtime command, which sets the cache expiration time.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 93cae350-9eac-3563-0a5a-661a080efbab
document_version_independent_id: c7b5932c-acf9-f266-3076-38be8133666a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-cache-and-setexpirationtime.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-cache-and-setexpirationtime
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-cache-and-setexpirationtime.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 78445c89-1539-c7c2-d43c-96722ed54656
---

# bitsadmin cache and setexpirationtime | Microsoft Learn

Sets the cache expiration time.

## Syntax

```
bitsadmin /cache /setexpirationtime secs
```

### Parameters

| Parameter | Description |
| --- | --- |
| secs | The number of seconds until the cache expires. |

## Examples

To set the cache to expire in 60 seconds:

```
bitsadmin /cache / setexpirationtime 60
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin cache command](bitsadmin-cache)