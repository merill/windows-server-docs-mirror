---
layout: Conceptual
title: bitsadmin util and version | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-util-and-version
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin util and version command, which displays the version of BITS service.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 5105e569-fcad-2c07-daf8-cc4076291107
document_version_independent_id: 9eb35b1c-cd86-59d8-8a42-fa7b38421b28
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-util-and-version.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-util-and-version
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-util-and-version.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 94fc2053-5ae2-0749-df7e-3192327e9651
---

# bitsadmin util and version | Microsoft Learn

Displays the version of BITS service (for example, 2.0).

Note

This command isn't supported by BITS 1.5 and earlier.

## Syntax

```
bitsadmin /util /version [/verbose]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /verbose | Use this switch to display the file version for each BITS-related DLL and to verify whether the BITS service can start. |

## Examples

To display the version of the BITS Service.

```
bitsadmin /util /version
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin util command](bitsadmin-util)
- [bitsadmin command](bitsadmin)