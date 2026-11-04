---
layout: Conceptual
title: fsutil objectid | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-objectid
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil objectid command, which manages object identifiers to track other objects such as files, directories, and links.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 622db606-f58d-31c5-7793-a927c2763a8e
document_version_independent_id: 4b1e3672-3960-fb02-ef2f-a273b868b9c8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-objectid.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-objectid
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-objectid.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ebf7daae-50be-4c4b-8d47-af6e3e530441
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b27bd7c0-0b2b-49fc-805f-6a916bb0e18e
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 703896dc-ba31-cec5-9b50-3aa160187656
---

# fsutil objectid | Microsoft Learn

Manages object identifiers (OIDs), which are internal objects used by the Distributed Link Tracking (DLT) Client service and File Replication Service (FRS), to track other objects such as files, directories, and links. Object identifiers are invisible to most programs and should never be modified.

Warning

Don't delete, set, or otherwise modify an object identifier. Deleting or setting an object identifier can result in the loss of data from portions of a file, up to and including entire volumes of data. In addition, you might cause adverse behavior in the Distributed Link Tracking (DLT) Client service and File Replication Service (FRS).

## Syntax

```
fsutil objectid [create] <filename>
fsutil objectid [delete] <filename>
fsutil objectid [query] <filename>
fsutil objectid [set] <objectID> <birthvolumeID> <birthobjectID> <domainID> <filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| create | Creates an object identifier if the specified file does not already have one. If the file already has an object identifier, this subcommand is equivalent to the **query** subcommand. |
| delete | Deletes an object identifier. |
| query | Queries an object identifier. |
| set | Sets an object identifier. |
| `<objectID>` | Sets a file-specific 16 byte hexadecimal identifier that is guaranteed to be unique within a volume. The object identifier is used by the Distributed Link Tracking (DLT) Client service and the File Replication Service (FRS) to identify files. |
| `<birthvolumeID>` | Indicates the volume on which the file was located when it first obtained an object identifier. This value is a 16-byte hexadecimal identifier that is used by the DLT Client service. |
| `<birthobjectID>` | Indicates the file's original object identifier (The *objectID* may change when a file is moved). This value is a 16-byte hexadecimal identifier that is used by the DLT Client service. |
| `<domainID>` | 16-byte hexadecimal domain identifier. This value isn't currently used and must be set to all zeros. |
| `<filename>` | Specifies the full path to the file including the file name and extension, for example *C:\documents\filename.txt*. |

#### Remarks

- Any file that has an object identifier also has a birth volume identifier, a birth object identifier, and a domain identifier. When you move a file, the object identifier may change, but the birth volume and birth object identifiers remain the same. This behavior enables the Windows operating system to always find a file, no matter where it has been moved.

### Examples

To create an object identifier, type:

`fsutil objectid create c:\temp\sample.txt`

To delete an object identifier, type:

`fsutil objectid delete c:\temp\sample.txt`

To query an object identifier, type:

`fsutil objectid query c:\temp\sample.txt`

To set an object identifier, type:

`fsutil objectid set 40dff02fc9b4d4118f120090273fa9fc f86ad6865fe8d21183910008c709d19e 40dff02fc9b4d4118f120090273fa9fc 00000000000000000000000000000000 c:\temp\sample.txt`

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)