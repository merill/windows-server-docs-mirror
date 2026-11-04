---
layout: Conceptual
title: fsutil dirty | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-dirty
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil dirty command, which queries or sets a volume's dirty bit.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f2f3d789-fb8d-f663-4ddb-57b97a3261a0
document_version_independent_id: c5bd5c74-97c0-ec87-b150-dc1ddaf581bf
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-dirty.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-dirty
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-dirty.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7254d210-a978-0272-fc07-008e9668e0b2
---

# fsutil dirty | Microsoft Learn

Queries or sets a volume's dirty bit. When a volume's dirty bit is set, **autochk** automatically checks the volume for errors the next time the computer is restarted.

## Syntax

```
fsutil dirty {query | set} <volumepath>
```

### Parameters

| Parameter | Description |
| --- | --- |
| query | Queries the specified volume's dirty bit. |
| set | Sets the specified volume's dirty bit. |
| `<volumepath>` | Specifies the drive name followed by a colon or GUID in the following format: `volume{GUID}`. |

#### Remarks

- A volume's dirty bit indicates that the file system may be in an inconsistent state. The dirty bit can be set because:

    - The volume is online and it has outstanding changes.
    - Changes were made to the volume and the computer was shut down before the changes were committed to the disk.
    - Corruption was detected on the volume.
- If the dirty bit is set when the computer restarts, **chkdsk** runs to verify the file system integrity and to attempt to fix any issues with the volume.

### Examples

To query the dirty bit on drive C, type:

```
fsutil dirty query c:
```

- If the volume is dirty, the following output displays: `Volume C: is dirty`
- If the volume isn't dirty, the following output displays: `Volume C: is not dirty`

To set the dirty bit on drive C, type:

```
fsutil dirty set C:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)