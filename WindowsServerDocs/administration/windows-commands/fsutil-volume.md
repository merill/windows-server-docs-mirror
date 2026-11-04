---
layout: Conceptual
title: fsutil volume | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-volume
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil volume command, which dismounts a volume, or queries the hard disk drive to determine how much free space is currently available on the hard disk drive or which file is using a particular cluster.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d717f946-0351-2df2-01e5-5b479e0ff379
document_version_independent_id: 5cba8e6d-acfd-7dd2-0b32-dda30cf4c60a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-volume.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-volume
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-volume.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 252bcb59-9ffd-1eea-d28f-ea2d2df05167
---

# fsutil volume | Microsoft Learn

Dismounts a volume, or queries the hard disk drive to determine how much free space is currently available on the hard disk drive or which file is using a particular cluster.

## Syntax

```
fsutil volume [allocationreport] <volumepath>
fsutil volume [diskfree] <volumepath>
fsutil volume [dismount] <volumepath>
fsutil volume [filelayout] <volumepath> <fileID>
fsutil volume [list]
fsutil volume [querycluster] <volumepath> <cluster> [<cluster>] …
```

### Parameters

| Parameter | Description |
| --- | --- |
| allocationreport | Displays information about how storage is used on a given volume. |
| `<volumepath>` | Specifies the drive letter (followed by a colon). |
| diskfree | Queries the hard disk drive to determine the amount of free space on it. |
| dismount | Dismounts a volume. |
| filelayout | Displays NTFS metadata for the given file. |
| `<fileID>` | Specifies the file id. |
| list | Lists all of the volumes on the system. |
| querycluster | Finds which file is using a specified cluster. You can specify multiple clusters with the **querycluster** parameter. |
| `<cluster>` | Specifies the logical cluster number (LCN). |

### Examples

To display an allocated clusters report, type:

```
fsutil volume allocationreport C:
```

To dismount a volume on drive C, type:

```
fsutil volume dismount c:
```

To query the amount of free space of a volume on drive C, type:

```
fsutil volume diskfree c:
```

To display all the information about a specified file(s), type:

```
fsutil volume C: *
fsutil volume C:\Windows
fsutil volume C: 0x00040000000001bf
```

To list the volumes on disk, type:

```
fsutil volume list
```

To find the file(s) that are using the clusters, specified by the logical cluster numbers 50 and 0x2000, on drive C, type:

```
fsutil volume querycluster C: 50 0x2000
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)
- [How NTFS Works](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc781134%28v=ws.10%29)