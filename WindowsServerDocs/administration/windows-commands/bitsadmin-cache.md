---
layout: Conceptual
title: bitsadmin cache | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-cache
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin cache command, which contains a list of the bitsadmin cache switches.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 5b1df11c-1e6b-6675-cb5b-5dd82fae30d2
document_version_independent_id: ea46c210-d37e-5f45-040c-20d9db648866
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-cache.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-cache
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-cache.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ea57465e-5ca4-2a1d-f300-4c7c1a53581e
---

# bitsadmin cache | Microsoft Learn

Contains a list of the bitsadmin /cache switches.

Contains a list of the bitsadmin /cache switches.

## Syntax

```
bitsadmin /cache /help
bitsadmin /cache /clear
bitsadmin /cache /delete
bitsadmin /cache /deleteURL
bitsadmin /cache /list
bitsadmin /cache /info
bitsadmin /cache /getlimit
bitsadmin /cache /setlimit
bitsadmin /cache /getexpirationtime
bitsadmin /cache /setexpirationtime
```

### Parameters

| Parameter | Description |
| --- | --- |
| [bitsadmin cache and help](bitsadmin-cache-and-help) | Displays the command-line usage for the /cache switches. |
| [bitsadmin cache and clear](bitsadmin-cache-clear) | Purges the local cache. |
| [bitsadmin cache and delete](bitsadmin-cache-and-delete) | Deletes a cache entry. |
| [bitsadmin cache and deleteURL](bitsadmin-cache-and-deleteurl) | Deletes all cache entries for the given URL. |
| [bitsadmin cache and list](bitsadmin-cache-and-list) | Lists all cache entries. |
| [bitsadmin cache and info](bitsadmin-cache-and-info) | Dumps a specific cache entry. |
| [bitsadmin cache and getlimit](bitsadmin-cache-and-getlimit) | Retrieves the cache limit. |
| [bitsadmin cache and setlimit](bitsadmin-cache-and-setlimit) | Sets the cache limit. |
| [bitsadmin cache and getexpirationtime](bitsadmin-cache-and-getexpirationtime) | Retrieves the cache expiration time. |
| [bitsadmin cache and setexpirationtime](bitsadmin-cache-and-setexpirationtime) | Sets the cache expiration time. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)