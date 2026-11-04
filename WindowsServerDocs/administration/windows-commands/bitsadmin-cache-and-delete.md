---
layout: Conceptual
title: bitsadmin cache and delete | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-cache-and-delete
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin cache and delete command, which deletes a specific cache entry.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 03fefc5c-432e-eb6d-17e6-8344eca7ee85
document_version_independent_id: a7f31811-1163-3682-0d94-5cf7fd57601b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-cache-and-delete.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-cache-and-delete
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-cache-and-delete.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fc4e73ca-b5f0-2fea-1d2c-8ac29469486a
---

# bitsadmin cache and delete | Microsoft Learn

Deletes a specific cache entry.

## Syntax

```
bitsadmin /cache /delete recordID
```

### Parameters

| Parameter | Description |
| --- | --- |
| recordID | The GUID associated with the cache entry. |

## Examples

To delete the cache entry with the RecordID of {6511FB02-E195-40A2-B595-E8E2F8F47702}:

```
bitsadmin /cache /delete {6511FB02-E195-40A2-B595-E8E2F8F47702}
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin cache command](bitsadmin-cache)