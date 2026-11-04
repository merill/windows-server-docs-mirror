---
layout: Conceptual
title: bitsadmin setmaxdownloadtime | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setmaxdownloadtime
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setmaxdownloadtime command, which sets the download timeout in seconds.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 3eaf9a42-1662-4309-daa7-8ff597e5b34b
document_version_independent_id: b98c7483-11c6-8442-b7c0-b6104ebb9db0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setmaxdownloadtime.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setmaxdownloadtime
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setmaxdownloadtime.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a75f2eac-8636-ee48-7a5f-898bfe7885e8
---

# bitsadmin setmaxdownloadtime | Microsoft Learn

Sets the download timeout in seconds.

## Syntax

```
bitsadmin /setmaxdownloadtime <job> <timeout>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| timeout | The length for the download timeout, in seconds. |

## Examples

To set the timeout for the job named *myDownloadJob* to 10 seconds.

```
bitsadmin /setmaxdownloadtime myDownloadJob 10
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)