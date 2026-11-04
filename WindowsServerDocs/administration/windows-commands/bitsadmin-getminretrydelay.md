---
layout: Conceptual
title: bitsadmin getminretrydelay | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-getminretrydelay
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin getminretrydelay command, which retrieves the length of time, in seconds, that the service waits after encountering a transient error before trying to transfer the file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: caa1916a-0291-ba11-0d72-405819be718a
document_version_independent_id: fb508853-4c4b-1aac-b289-c1414e36c65d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-getminretrydelay.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-getminretrydelay
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-getminretrydelay.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 51622bbd-60f9-3b70-dc00-cc4692f4f1cc
---

# bitsadmin getminretrydelay | Microsoft Learn

Retrieves the length of time, in seconds, that the service will wait after encountering a transient error before trying to transfer the file.

## Syntax

```
bitsadmin /getminretrydelay <job>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |

## Examples

To retrieve the minimum retry delay for the job named *myDownloadJob*:

```
bitsadmin /getminretrydelay myDownloadJob
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)