---
layout: Conceptual
title: Fsutil fsinfo | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-fsinfo
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil fsinfo command, which lists all drives, queries the drive type, queries volume information, queries NTFS-specific volume information, or queries file system statistics.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 2d893673-3acf-929e-393a-8cc5ca969e90
document_version_independent_id: 27ce97cb-9552-e727-d6d1-ce9359072cb4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-fsinfo.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-fsinfo
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-fsinfo.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5aa3528a-ccbb-3f6f-3cca-598cffa3d04b
---

# Fsutil fsinfo | Microsoft Learn

Lists all drives, queries the drive type, queries volume information, queries NTFS-specific volume information, or queries file system statistics.

## Syntax

```
fsutil fsinfo [drives]
fsutil fsinfo [drivetype] <volumepath>
fsutil fsinfo [ntfsinfo] <rootpath>
fsutil fsinfo [statistics] <volumepath>
fsutil fsinfo [volumeinfo] <rootpath>
```

### Parameters

| Parameter | Description |
| --- | --- |
| drives | Lists all drives in the computer. |
| drivetype | Queries a drive and lists its type, for example CD-ROM drive. |
| ntfsinfo | Lists NTFS specific volume information for the specified volume, such as the number of sectors, total clusters, free clusters, and the start and end of the MFT Zone. |
| sectorinfo | Lists information about the hardware's sector size and alignment. |
| statistics | Lists file system statistics for the specified volume, such as metadata, log file, and MFT reads and writes. |
| volumeinfo | Lists information for the specified volume, such as the file system, and whether the volume supports case-sensitive file names, unicode in file names, disk quotas, or is a DirectAccess (DAX) volume. |
| `<volumepath>:` | Specifies the drive letter (followed by a colon). |
| `<rootpath>:` | Specifies the drive letter (followed by a colon) of the root drive. |

### Examples

To list all of the drives in the computer, type:

```
fsutil fsinfo drives
```

Output similar to the following displays:

```
Drives: A:\ C:\ D:\ E:\
```

To query the drive type of drive C, type:

```
fsutil fsinfo drivetype c:
```

Possible results of the query include:

```
Unknown Drive
No such Root Directory
Removable Drive, for example floppy
Fixed Drive
Remote/Network Drive
CD-ROM Drive
Ram Disk
```

To query the volume information for volume E, type:

```
fsutil fsinfo volumeinfo e:
```

Output similar to the following displays:

```
Volume Name : Volume
Serial Number : 0xd0b634d9
Max Component Length : 255
File System Name : NTFS
Supports Named Streams
Is DAX Volume
```

To query drive F for NTFS-specific volume information, type:

```
fsutil fsinfo ntfsinfo f:
```

Output similar to the following displays:

```
NTFS Volume Serial Number : 0xe660d46a60d442cb
Number Sectors : 0x00000000010ea04f
Total Clusters : 0x000000000021d409
Mft Zone End : 0x0000000000004700
```

To query the file system's underlying hardware for sector information, type:

```
fsutil fsinfo sectorinfo d:
```

Output similar to the following displays:

```
D:\>fsutil fsinfo sectorinfo d:
LogicalBytesPerSector : 4096
PhysicalBytesPerSectorForAtomicity : 4096
Trim Not Supported
DAX capable
```

To query the file system statistics for drive E, type:

```
fsutil fsinfo statistics e:
```

Output similar to the following displays:

```
File System Type : NTFS
Version : 1
UserFileReads : 75021
UserFileReadBytes : 1305244512
LogFileWriteBytes : 180936704
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)