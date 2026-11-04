---
layout: Conceptual
title: Set context | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/set-context
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the set context command, which sets the context for shadow copy creation.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ba12ebe0-fc8d-6353-8f37-482507a51e4e
document_version_independent_id: cc9deb71-e8e6-05bf-a10e-6a431e682fab
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/set-context.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/set-context
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/set-context.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 3788d9a5-64a7-cab5-ec05-52c816cd0e27
---

# Set context | Microsoft Learn

Sets the context for shadow copy creation. If used without parameters, **set context** displays help at the command prompt.

## Syntax

```
set context {clientaccessible | persistent [nowriters] | volatile [nowriters]}
```

### Parameters

| Parameter | Description |
| --- | --- |
| clientaccessible | Specifies that the shadow copy is usable by client versions of Windows. This context is persistent by default. |
| persistent | Specifies that the shadow copy persists across program exit, reset, or restart. |
| volatile | Deletes the shadow copy on exit or reset. |
| nowriters | Specifies that all writers are excluded. |

## Examples

To prevent shadow copies from being deleted when you exit DiskShadow, type:

```
set context persistent
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [set metadata command](set-metadata)
- [set option command](set-option)
- [set verbose command](set-verbose)