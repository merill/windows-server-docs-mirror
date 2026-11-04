---
layout: Conceptual
title: compact vdisk | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/compact-vdisk
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the compact vdisk command, which reduces the physical size of a dynamically expanding virtual hard disk (VHD) file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: fe70f545-3990-d194-ba4c-79134a972e15
document_version_independent_id: 3b452579-16c2-2935-ba45-ab7ccd719186
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/compact-vdisk.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/compact-vdisk
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/compact-vdisk.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 780e53bb-307b-a50d-4896-c326637dd2da
---

# compact vdisk | Microsoft Learn

Reduces the physical size of a dynamically expanding virtual hard disk (VHD) file. This parameter is useful because dynamically expanding VHDs increase in size as you add files, but they do not automatically reduce in size when you delete files.

## Syntax

```
compact vdisk
```

### Remarks

- A dynamically expanding VHD must be selected for this operation to succeed. Use the [select vdisk command](select-vdisk) to select a VHD and shift the focus to it.
- You can only use compact dynamically expanding VHDs that are detached or attached as read-only.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [attach vdisk command](attach-vdisk)
- [detail vdisk command](detail-vdisk)
- [Detach vdisk command](detach-vdisk)
- [expand vdisk command](expand-vdisk)
- [Merge vdisk command](merge-vdisk)
- [select vdisk command](select-vdisk)
- [list command](list)