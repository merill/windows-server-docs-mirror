---
layout: Conceptual
title: set metadata | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/set-metadata
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the set metadata command, which sets the name and location of the shadow creation metadata file used to transfer shadow copies from one computer to another.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: eb08658d-1f6a-3e1e-8979-0e84940efbbc
document_version_independent_id: 612cd324-cf80-1015-6ac6-4ad7b1181ac0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/set-metadata.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/set-metadata
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/set-metadata.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f6a28f9e-6e22-338a-e85b-7328cf094709
---

# set metadata | Microsoft Learn

Sets the name and location of the shadow creation metadata file used to transfer shadow copies from one computer to another. If used without parameters, **set metadata** displays help at the command prompt.

## Syntax

```
set metadata [<drive>:][<path>]<metadata.cab>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<drive>:][<path>]` | Specifies the location to create the metadata file. |
| `<metadata.cab>` | Specifies the name of the cab file to store shadow creation metadata. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [set context command](set-context)
- [set option command](set-option)
- [set verbose command](set-verbose)