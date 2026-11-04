---
layout: Conceptual
title: bitsadmin getreplyfilename | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-getreplyfilename
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin getreplyfilename command, which gets the path of the file that contains the server upload-reply for the job.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 2b2f9aef-d4c5-35cf-1f78-c1b2729cfddb
document_version_independent_id: 92627187-9a26-2c7e-7610-4c316de03687
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-getreplyfilename.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-getreplyfilename
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-getreplyfilename.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: faa6506c-31ef-2e00-6ddd-f31ae36145cb
---

# bitsadmin getreplyfilename | Microsoft Learn

Gets the path of the file that contains the server upload-reply for the job.

Note

This command isn't supported by BITS 1.2 and earlier.

## Syntax

```
bitsadmin /getreplyfilename <job>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |

## Examples

To retrieve the upload-reply filename for the job named *myDownloadJob*:

```
bitsadmin /getreplyfilename myDownloadJob
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)