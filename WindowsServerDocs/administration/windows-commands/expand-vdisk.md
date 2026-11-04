---
layout: Conceptual
title: expand vdisk | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/expand-vdisk
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the expand vdisk command, which expands a virtual hard disk (VHD) to a specified size.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d4bf76f3-73e6-1d63-641f-847ca717bf18
document_version_independent_id: dbfd6085-572c-e6d7-1b67-d993beea1927
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/expand-vdisk.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/expand-vdisk
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/expand-vdisk.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 25da9d7c-d324-647c-db5a-8b1b41602117
---

# expand vdisk | Microsoft Learn

Expands a virtual hard disk (VHD) to a specified size.

A VHD must be selected and detached for this operation to succeed. Use the [select vdisk command](select-vdisk) to select a volume and shift the focus to it.

## Syntax

```
expand vdisk maximum=<n>
```

### Parameters

| Parameter | Description |
| --- | --- |
| maximum=`<n>` | Specifies the new size for the VHD in megabytes (MB). |

### Examples

To expand the selected VHD to 20 GB, type:

```
expand vdisk maximum=20000
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select vdisk command](select-vdisk)
- [attach vdisk command](attach-vdisk)
- [compact vdisk command](compact-vdisk)
- [detach vdisk command](detach-vdisk)
- [detail vdisk command](detail-vdisk)
- [merge vdisk command](merge-vdisk)
- [list command](list)