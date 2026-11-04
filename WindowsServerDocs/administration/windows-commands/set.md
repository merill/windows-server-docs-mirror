---
layout: Conceptual
title: set commands | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/set
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the set commands, which sets the context, options, verbose mode, and metadata file for shadow copy creation.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4b224e61-7f5c-751a-3c21-3af5418083f0
document_version_independent_id: b0b8cf60-c1de-2ce6-5bdb-dd1eeb009101
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/set.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/set
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/set.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 77448888-3fb1-3580-8692-6388c3cd4360
---

# set commands | Microsoft Learn

Sets the context, options, verbose mode, and metadata file for shadow copy creation. If used without parameters, **set** lists all current settings.

## Syntax

```
set
set context
set option
set verbose
set metadata
```

### Parameters

| Parameters | Description |
| --- | --- |
| [set context](set-context) | Sets the context for shadow copy creation. |
| [set metadata](set-metadata) | Sets the name and location of the shadow creation metadata file. |
| [set option](set-option) | Sets options for shadow copy creation. |
| [set verbose](set-verbose) | Turns the verbose output mode on or off. |
| /? | Displays help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)