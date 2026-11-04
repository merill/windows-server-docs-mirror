---
layout: Conceptual
title: detail | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/detail
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the detail command, which displays information about the selected disk, partition, volume, or virtual hard disk (VHD).
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a7041045-1580-02c3-59fd-5b8b6920d8c9
document_version_independent_id: 37abf963-b62c-8167-4662-088dbafff7a7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/detail.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/detail
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/detail.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 280a99be-7d9a-810a-fa91-f2c1ef97241c
---

# detail | Microsoft Learn

Displays information about the selected disk, partition, volume, or virtual hard disk (VHD).

## Syntax

```
detail disk
detail partition
detail volume
detail vdisk
```

### Parameters

| Parameter | Description |
| --- | --- |
| [Detail disk](detail-disk) | Displays the properties of the selected disk and the volumes on that disk. |
| [Detail partition](detail-partition) | Displays the properties of the selected partition. |
| [Detail volume](detail-volume) | Displays the disks on which the current volume resides. |
| [Detail vdisk](detail-vdisk) | Displays the properties of the selected VHD. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)