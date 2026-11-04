---
layout: Conceptual
title: bitsadmin setminretrydelay | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setminretrydelay
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setminretrydelay command, which sets the minimum length of time, in seconds, that BITS waits after encountering a transient error before trying to transfer the file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7cc077e0-374b-765f-69f1-7070535c36d7
document_version_independent_id: b3fa34bf-1178-9b6a-2d26-6e62a3c32b79
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setminretrydelay.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setminretrydelay
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setminretrydelay.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8a19c946-bafc-aa84-0067-31976db8e499
---

# bitsadmin setminretrydelay | Microsoft Learn

Sets the minimum length of time, in seconds, that BITS waits after encountering a transient error before trying to transfer the file.

## Syntax

```
bitsadmin /setminretrydelay <job> <retrydelay>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| retrydelay | Minimum length of time for BITS to wait after an error during transfer, in seconds. |

## Examples

To set the minimum retry delay to 35 seconds for the job named *myDownloadJob*:

```
bitsadmin /setminretrydelay myDownloadJob 35
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)