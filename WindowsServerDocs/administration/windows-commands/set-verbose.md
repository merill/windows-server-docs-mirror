---
layout: Conceptual
title: set verbose | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/set-verbose
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the set verbose command, which specifies whether verbose output is provided during shadow copy creation.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 98c91746-0444-fe60-9d08-e71493f528d8
document_version_independent_id: 815db0bd-ecef-b67e-80a3-b67954c410ec
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/set-verbose.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/set-verbose
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/set-verbose.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c400b2dd-f704-f96b-de2e-bd797a2d3609
---

# set verbose | Microsoft Learn

Specifies whether verbose output is provided during shadow copy creation. If used without parameters, **set verbose** displays help at the command prompt.

## Syntax

```
set verbose {on | off}
```

### Parameters

| Parameter | Description |
| --- | --- |
| on | Turns on verbose output logging during the shadow copy creation process. If verbose mode is on, **set** provides details of writer inclusion or exclusion and details of metadata compression and extraction. |
| off | Turns off verbose output logging during the shadow copy creation process. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [set context command](set-context)
- [set metadata command](set-metadata)
- [set option command](set-option)