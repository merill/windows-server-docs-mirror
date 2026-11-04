---
layout: Conceptual
title: bitsadmin setpeercachingflags | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setpeercachingflags
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setpeercachingflags command, which sets flags that determine if the files of the job can be cached and served to peers and if the job can download content from peers.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 07112d96-fc1a-d980-38b4-f18c029c9690
document_version_independent_id: 6ef90429-a72a-5fff-63f1-ed6143a8212b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setpeercachingflags.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setpeercachingflags
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setpeercachingflags.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 159d1e52-13b9-f368-629d-ec977e79a40c
---

# bitsadmin setpeercachingflags | Microsoft Learn

Sets flags that determine if the files of the job can be cached and served to peers and if the job can download content from peers.

## Syntax

```
bitsadmin /setpeercachingflags <job> <value>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| value | An unsigned integer, including:<br>- **1.** The job can download content from peers.<br>- **2.** The files of the job can be cached and served to peers. |

## Examples

To allow the job named *myDownloadJob* to download content from peers:

```
bitsadmin /setpeercachingflags myDownloadJob 1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)