---
layout: Conceptual
title: fsutil file | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-file
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil file command, which finds a file by user name, queries allocated ranges for a file, sets a file's short name, sets a file's valid data length, sets zero data for a file, or creates a new file.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e18545fd-4776-a954-51c5-778d88ac78e4
document_version_independent_id: 93f39f76-6411-d4af-a268-a7b768272e82
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-file.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-file.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ab322ade-8905-391a-9681-33f22bf52f7d
---

# fsutil file | Microsoft Learn

Finds a file by user name (if Disk Quotas are enabled), queries allocated ranges for a file, sets a file's short name, sets a file's valid data length, sets zero data for a file, or creates a new file.

## Syntax

```
fsutil file [createnew] <filename> <length>
fsutil file [findbysid] <username> <directory>
fsutil file [optimizemetadata] [/A] <filename>
fsutil file [queryallocranges] offset=<offset> length=<length> <filename>
fsutil file [queryextents] [/R] <filename> [<startingvcn> [<numvcns>]]
fsutil file [queryfileid] <filename>
fsutil file [queryfilenamebyid] <volume> <fileid>
fsutil file [queryoptimizemetadata] <filename>
fsutil file [queryvaliddata] [/R] [/D] <filename>
fsutil file [seteof] <filename> <length>
fsutil file [setshortname] <filename> <shortname>
fsutil file [setvaliddata] <filename> <datalength>
fsutil file [setzerodata] offset=<offset> length=<length> <filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| createnew | Creates a file of the specified name and size, with content that consists of zeroes. |
| `<length>` | Specifies the file's valid data length. |
| findbysid | Finds files that belong to a specified user on NTFS volumes where Disk Quotas are enabled. |
| `<username>` | Specifies the user's user name or logon name. |
| `<directory>` | Specifies the full path to the directory, for example C:\users. |
| optimizemetadata | This performs an immediate compaction of the metadata for a given file. |
| /a | Analyze file metadata before and after optimization. |
| queryallocranges | Queries the allocated ranges for a file on an NTFS volume. Useful for determining whether a file has sparse regions. |
| offset=`<offset>` | Specifies the start of the range that should be set to zeroes. |
| length=`<length>` | Specifies the length of the range (in bytes). |
| queryextents | Queries extents for a file. |
| /r | If `<filename>` is a reparse point, open it rather than its target. |
| `<startingvcn>` | Specifies first VCN to query. If omitted, start at VCN 0. |
| `<numvcns>` | Number of VCNs to query. If omitted or 0, query until EOF. |
| queryfileid | Queries the file ID of a file on an NTFS volume. |
| `<volume>` | Specifies the volume as drive name followed by a colon. |
| queryfilenamebyid | Displays a random link name for a specified file ID on an NTFS volume. Since a file can have more than one link name pointing to that file, it is not guaranteed which file link will be provided as a result of the query for the file name. |
| `<fileid>` | Specifies the ID of the file on an NTFS volume. |
| queryoptimizemetadata | Queries the metadata state of a file. |
| queryvaliddata | Queries the valid data length for a file. |
| /d | Display detailed valid data information. |
| seteof | Sets the EOF of the given file. |
| setshortname | Sets the short name (8.3 character-length file name) for a file on an NTFS volume. |
| `<shortname>` | Specifies the file's short name. |
| setvaliddata | Sets the valid data length for a file on an NTFS volume. |
| `<datalength>` | Specifies the length of the file in bytes. |
| setzerodata | Sets a range (specified by *offset* and *length*) of the file to zeroes, which empties the file. If the file is a sparse file, the underlying allocation units are decommitted. |

#### Remarks

- In NTFS, there are two important concepts of file length: the end-of-file (EOF) marker and the Valid Data Length (VDL). The EOF indicates the actual length of the file. The VDL identifies the length of valid data on disk. Any reads between VDL and EOF automatically return 0 to preserve the C2 object reuse requirement.
- The **setvaliddata** parameter is only available for administrators because it requires the Perform volume maintenance tasks (SeManageVolumePrivilege) privilege. This feature is only required for advanced multimedia and system area network scenarios. The **setvaliddata** parameter must be a positive value that is greater than the current VDL, but less than the current file size.

    It is useful for programs to set a VDL when:

    - Writing raw clusters directly to disk through a hardware channel. This allows the program to inform the file system that this range contains valid data that can be returned to the user.
    - Creating large files when performance is an issue. This avoids the time it takes to fill the file with zeroes when the file is created or extended.

### Examples

To find files that are owned by *scottb* on drive C, type:

```
fsutil file findbysid scottb c:\users
```

To query the allocated ranges for a file on an NTFS volume, type:

```
fsutil file queryallocranges offset=1024 length=64 c:\temp\sample.txt
```

To optimize metadata for a file, type:

```
fsutil file optimizemetadata C:\largefragmentedfile.txt
```

To query the extents for a file, type:

```
fsutil file queryextents C:\Temp\sample.txt
```

To set the EOF for a file, type:

```
fsutil file seteof C:\testfile.txt 1000
```

To set the short name for the file, *longfilename.txt* on drive C to *longfile.txt*, type:

```
fsutil file setshortname c:\longfilename.txt longfile.txt
```

To set the valid data length to *4096 bytes* for a file named *testfile.txt* on an NTFS volume, type:

```
fsutil file setvaliddata c:\testfile.txt 4096
```

To set a range of a file on an NTFS volume to zeros to empty it, type:

```
fsutil file setzerodata offset=100 length=150 c:\temp\sample.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)