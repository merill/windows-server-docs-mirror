---
layout: Conceptual
title: bitsadmin getfilestransferred | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-getfilestransferred
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin getfilestransferred command, which retrieves the number of files transferred for the specified job.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: cb1d149c-e1d4-eaf6-dfa8-10349ab5a2cc
document_version_independent_id: 451c61b5-ddea-f8bb-cefc-e110b0444abd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-getfilestransferred.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-getfilestransferred
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-getfilestransferred.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d7d16d3f-74f5-997d-a633-d26ac1205978
---

# bitsadmin getfilestransferred | Microsoft Learn

Retrieves the number of files transferred for the specified job.

## Syntax

```
bitsadmin /getfilestransferred <job>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |

## Examples

To retrieve the number of files transferred in the job named *myDownloadJob*:

```
bitsadmin /getfilestransferred myDownloadJob
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)