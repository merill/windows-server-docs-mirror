---
layout: Conceptual
title: bitsadmin setcustomheaders | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setcustomheaders
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setcustomheaders command, which adds a custom HTTP header to a GET request.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4f9e7e44-2d21-a872-a923-ffe88562925c
document_version_independent_id: 355e7b33-0798-0107-4ee4-0252b470bfa3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setcustomheaders.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setcustomheaders
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setcustomheaders.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 752d2f1d-603c-9b45-f7ea-8ad697dcbbef
---

# bitsadmin setcustomheaders | Microsoft Learn

Add a custom HTTP header to a GET request sent to an HTTP server. For more information about GET requests, see [Method Definitions](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.3) and [Header Field Definitions](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html).

## Syntax

```
bitsadmin /setcustomheaders <job> <header1> <header2> <...>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| `<header1> <header2>` and so on | The custom headers for the job. |

## Examples

To add a custom HTTP header for the job named *myDownloadJob*:

```
bitsadmin /setcustomheaders myDownloadJob accept-encoding:deflate/gzip
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)