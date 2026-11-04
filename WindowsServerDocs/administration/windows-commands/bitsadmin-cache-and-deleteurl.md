---
layout: Conceptual
title: bitsadmin cache and deleteURL | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-cache-and-deleteurl
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin cache and deleteURL command, which deletes all cache entries for the given URL.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: af20615d-cc1f-6d4c-1d28-4fe9e334ae3c
document_version_independent_id: a819339d-84fc-350f-344b-7b0686a6a81b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-cache-and-deleteurl.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-cache-and-deleteurl
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-cache-and-deleteurl.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e58e0aad-023e-6798-a672-f22932dc5455
---

# bitsadmin cache and deleteURL | Microsoft Learn

Deletes all cache entries for the given URL.

## Syntax

```
bitsadmin /deleteURL URL
```

### Parameters

| Parameter | Description |
| --- | --- |
| URL | The Uniform Resource Locator that identifies a remote file. |

## Examples

To delete all cache entries for `https://www.contoso.com/en/us/default.aspx`:

```
bitsadmin /deleteURL https://www.contoso.com/en/us/default.aspx
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin cache command](bitsadmin-cache)