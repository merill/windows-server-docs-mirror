---
layout: Conceptual
title: reg import | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reg-import
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the reg import command, which copies the contents of a file that contains exported registry subkeys, entries, and values into the registry of the local computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-10-20T00:00:00.0000000Z
locale: en-us
document_id: 6472b04a-6012-bb34-1d0e-c03fc4504f19
document_version_independent_id: 00f23c12-7136-078f-8708-47380f9872a2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reg-import.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reg-import
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reg-import.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cdec5767-3d5f-cfab-d3d0-f2a5c406e3d3
---

# reg import | Microsoft Learn

Copies the contents of a file that contains exported registry subkeys, entries, and values into the registry of the local computer.

## Syntax

```
reg import <filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<filename>` | Specifies the name and path of the file that has content to be copied into the registry of the local computer. This file must be created in advance by using **reg export**. |
| `/reg:32` | Specifies the key should be accessed using the 32-bit registry view. |
| `/reg:64` | Specifies the key should be accessed using the 64-bit registry view. |
| /? | Displays help at the command prompt. |

#### Remarks

- The return values for the **reg import** operation are:

    | Value | Description |
    | --- | --- |
    | 0 | Success |
    | 1 | Failure |

### Examples

To import registry entries from the file named AppBkUp.reg, type:

```
reg import AppBkUp.reg
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [reg export command](reg-export)