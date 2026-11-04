---
layout: Conceptual
title: bitsadmin cache and setlimit | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-cache-and-setlimit
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin cache and setlimit command, which sets the cache size limit.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7ae2b6ad-a587-27ff-d94f-96b4696a4f6b
document_version_independent_id: efccead6-617c-2a3c-9191-52e1adce73d1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-cache-and-setlimit.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-cache-and-setlimit
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-cache-and-setlimit.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 400b6355-ff84-2ccc-a002-5e0b35d8e246
---

# bitsadmin cache and setlimit | Microsoft Learn

Sets the cache size limit.

## Syntax

```
bitsadmin /cache /setlimit percent
```

### Parameters

| Parameter | Description |
| --- | --- |
| percent | The cache limit defined as a percentage of the total hard disk space. |

## Examples

To set the cache size limit to 50%:

```
bitsadmin /cache /setlimit 50
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin cache command](bitsadmin-cache)