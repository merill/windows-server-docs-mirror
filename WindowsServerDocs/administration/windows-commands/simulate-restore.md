---
layout: Conceptual
title: simulate restore | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/simulate-restore
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the simulate restore command, which tests whether writer involvement in restore sessions will be successful on the computer without issuing PreRestore or PostRestore events to writers.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 11154948-f78b-ab0d-f2a2-53d55a4c97bf
document_version_independent_id: 31ba4e39-abbe-d5fc-d130-0f957b474232
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/simulate-restore.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/simulate-restore
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/simulate-restore.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 921cb53e-1f3e-d87e-e8c0-f9ad69dfbd13
---

# simulate restore | Microsoft Learn

Tests whether writer involvement in restore sessions will be successful on the computer without issuing **PreRestore** or **PostRestore** events to writers.

Note

A DiskShadow metadata file must be selected for the **simulate restore** command to succeed. Use the [load metadata command](load-metadata) to load the selected writers and components for the restore.

## Syntax

```
simulate restore
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [load metadata command](load-metadata)