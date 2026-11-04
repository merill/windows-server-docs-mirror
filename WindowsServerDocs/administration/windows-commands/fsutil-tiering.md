---
layout: Conceptual
title: fsutil tiering | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-tiering
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil tiering command, which enables management of storage tier functions, such as setting and disabling flags and listing of tiers.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c94757eb-4f57-a161-9d22-eb22dd67e027
document_version_independent_id: 45423d1a-418a-9d94-022b-b7d0712e4220
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-tiering.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-tiering
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-tiering.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fb11a8d6-d2c0-9682-04c7-107490a4b8a3
---

# fsutil tiering | Microsoft Learn

Enables management of storage tier functions, such as setting and disabling flags and listing of tiers.

## Syntax

```
fsutil tiering [clearflags] <volume> <flags>
fsutil tiering [queryflags] <volume>
fsutil tiering [regionlist] <volume>
fsutil tiering [setflags] <volume> <flags>
fsutil tiering [tierlist] <volume>
```

### Parameters

| Parameter | Description |
| --- | --- |
| clearflags | Disables the tiering behavior flags of a volume. |
| `<volume>` | Specifies the volume. |
| /trnh | For volumes with tiered storage, causes Heat gathering to be disabled.<br>Applies to NTFS and ReFS only. |
| queryflags | Queries the tiering behavior flags of a volume. |
| regionlist | Lists the tiered regions of a volume and their respective storage tiers. |
| setflags | Enables the tiering behavior flags of a volume. |
| tierlist | Lists the storage tiers associated with a volume. |

### Examples

To query the flags on volume C, type:

```
fsutil tiering queryflags C:
```

To set the flags on volume C, type:

```
fsutil tiering setflags C: /trnh
```

To clear the flags on volume C, type:

```
fsutil tiering clearflags C: /trnh
```

To list the regions of volume C and their respective storage tiers, type:

```
fsutil tiering regionlist C:
```

To list the tiers of volume C, type:

```
fsutil tiering tierlist C:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)