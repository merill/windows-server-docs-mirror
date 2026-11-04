---
layout: Conceptual
title: set option | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/set-option
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the set option command, which sets the options for shadow copy creation.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ae501172-bda1-05a8-b2a7-5d5e18cf99d2
document_version_independent_id: 4817742e-5fda-4fb1-3f94-9fb0d5622141
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/set-option.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/set-option
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/set-option.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f0455778-917a-48a8-ee50-62256bd2dd13
---

# set option | Microsoft Learn

Sets the options for shadow copy creation. If used without parameters, **set option** displays help at the command prompt.

## Syntax

```
set option {[differential | plex] [transportable] [[rollbackrecover] [txfrecover] | [noautorecover]]}
```

### Parameters

| Parameter | Description |
| --- | --- |
| [differential] | Specifies to create a point-in-time snapshot of specified volumes. |
| [plex] | Specifies to create a point-in-time clone copy of the data on a specified volume. |
| [transportable] | Specifies that the shadow copy is not to be imported yet. The metadata .cab file can later be used to import the shadow copy to the same or a different computer. |
| [rollbackrecover] | Signals writers to use *autorecover* during the **PostSnapshot** event. This is useful if the shadow copy will be used for rollback (for example, with data mining). |
| [txfrecover] | Requests VSS to make the shadow copy transactionally consistent during creation. |
| [noautorecover] | Stops writers and the file system from performing any recovery changes to the shadow copy to a transactionally consistent state. **Noautorecover** can't be used with **txfrecover** or **rollbackrecover**. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [set context command](set-context)
- [set metadata command](set-metadata)
- [set verbose command](set-verbose)