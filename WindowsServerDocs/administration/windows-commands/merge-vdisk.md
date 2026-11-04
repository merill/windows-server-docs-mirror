---
layout: Conceptual
title: merge vdisk | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/merge-vdisk
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the merge vdisk command, which merges a differencing virtual hard disk (VHD) with its corresponding parent VHD.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 011bbfc9-cb8a-f65b-bb23-a5acde9daff6
document_version_independent_id: 55c2f699-e75f-1f13-6cdb-eb81efdcdc2a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/merge-vdisk.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/merge-vdisk
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/merge-vdisk.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2cc7fe0e-3f51-252e-7498-08b046371c04
---

# merge vdisk | Microsoft Learn

Merges a differencing virtual hard disk (VHD) with its corresponding parent VHD. The parent VHD will be modified to include the modifications from the differencing VHD. This command modifies the parent VHD. As a result, other differencing VHDs that are dependent on the parent will no longer be valid.

Important

You must choose and detach a VHD for this operation to succeed. Use the **select vdisk** command to select a VHD and shift the focus to it.

## Syntax

```
merge vdisk depth=<n>
```

### Parameters

| Parameter | Description |
| --- | --- |
| depth=`<n>` | Indicates the number of parent VHD files to merge together. For example, `depth=1` indicates that the differencing VHD will be merged with one level of the differencing chain. |

### Examples

To merge a differencing VHD with its parent VHD, type:

```
merge vdisk depth=1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [attach vdisk command](attach-vdisk)
- [compact vdisk command](compact-vdisk)
- [detail vdisk command](detail-vdisk)
- [detach vdisk command](detach-vdisk)
- [expand vdisk command](expand-vdisk)
- [select vdisk command](select-vdisk)
- [list command](list)