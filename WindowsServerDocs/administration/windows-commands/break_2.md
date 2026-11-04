---
layout: Conceptual
title: break (diskshadow) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/break_2
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the break command, which disassociates a shadow copy volume from VSS and makes it accessible as a regular volume.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-10-12T00:00:00.0000000Z
locale: en-us
document_id: baebc3ab-d865-72ea-17ec-a5fc2410e267
document_version_independent_id: 2f3ea382-5b2d-2f8e-5ee8-4db851e242c9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/break_2.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/break_2
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/break_2.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 78987e52-1dac-e5d7-e447-0f69269ae644
---

# break (diskshadow) | Microsoft Learn

Disassociates a shadow copy volume from VSS and makes it accessible as a regular volume. The volume can then be accessed using a drive letter (if assigned) or volume name. If used without parameters, **break** displays help at the command prompt.

Note

This command is relevant only for hardware shadow copies after import.

Exposed volumes, like the shadow copies they originate from, are read-only by default. Access to the volume is made directly to the hardware provider without record of the volume having been a shadow copy.

## Syntax

```
break [writable] <setid>
```

### Parameters

| Parameter | Description |
| --- | --- |
| writable | Enables read/write access on the volume. |
| `<setid>` | Specifies the ID of the shadow copy set. The alias of the shadow copy ID, which is stored as an environment variable by the **load metadata** command, can be used in the *SetID* parameter. |

## Examples

To make a shadow copy using the alias name Alias1 accessible as a writable volume in the operating system:

```
break writable %Alias1%
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)