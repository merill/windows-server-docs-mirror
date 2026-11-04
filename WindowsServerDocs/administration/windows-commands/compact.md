---
layout: Conceptual
title: compact | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/compact
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the compact command, which displays or alters the compression of files or directories on NTFS partitions.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: eaddfdd0-36f0-5188-4ccc-534227c91149
document_version_independent_id: 9a9901e1-9c4c-c623-936d-e55de1c22dbe
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/compact.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/compact
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/compact.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c793e1b2-57d8-57c5-972e-a3cac4236a2d
---

# compact | Microsoft Learn

Displays or alters the compression of files or directories on NTFS partitions. If used without parameters, **compact** displays the compression state of the current directory and any files it contains.

## Syntax

```
compact [/C | /U] [/S[:dir]] [/A] [/I] [/F] [/Q] [/EXE[:algorithm]] [/CompactOs[:option] [/windir:dir]] [filename [...]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /c | Compresses the specified directory or file. Directories are marked so any files added afterwards are compressed, unless the /EXE parameter is specified. |
| /u | Uncompresses the specified directory or file. Directories are marked so any files added afterwards aren't compressed. If the /EXE parameter is specified, only files compressed as executables are uncompressed; if you don't specify the /EXE parameter, only NTFS compressed files are uncompressed. |
| /s`[:<dir>]` | Performs the chosen operation on files in the specified directory and all subdirectories. By default, the current directory is used as the `<dir>` value. |
| /a | Displays hidden or system files. By default, these files aren't included. |
| /i | Continues performing the specified operation, ignoring errors. By default, this command stops when an error is encountered. |
| /f | Forces compression or uncompression of the specified directory or file. Already-compressed files are skipped by default. The **/f** parameter is used in the case of a file that was partly compressed when the operation was interrupted by a system crash. To force the file to be compressed in its entirety, use the **/c** and **/f** parameters and specify the partially compressed file. |
| /q | Reports only the most essential information. |
| /EXE | Uses compression optimized for executable files that are read frequently, but not modified. Supported algorithms are:<br>- **XPRESS4K** (fastest and default value)<br>- **XPRESS8K**<br>- **XPRESS16K**<br>- **LZX** (most compact) |
| /CompactOs | Sets or queries the system's compression state. Supported options are:<br>- **query** - Queries the system's **Compact** state.<br>- **always** - Compresses all operating system binaries and sets the system state to Compact, which remains unless administrator changes it.<br>- **never** - Uncompresses all operating system binaries and sets the system state to non-Compact, which remains unless administrator changes it. |
| /windir | Used with the **/CompactOs:query** parameter, when querying the offline operating system. Specifies the directory where Windows is installed. |
| `<filename>` | Specifies a pattern, file, or directory. You can use multiple file names, and the **\*** and **?** wildcard characters. |
| /? | Displays help at the command prompt. |

#### Remarks

- This command is the command-line version of the NTFS file system compression feature. The compression state of a directory indicates whether files are automatically compressed when they are added to the directory. Setting the compression state of a directory does not necessarily change the compression state of files that are already in the directory.
- You can't use this command to read, write, or mount volumes compressed using DriveSpace or DoubleSpace. You also can't use this command to compress file allocation table (FAT) or FAT32 partitions.

## Examples

To set the compression state of the current directory, its subdirectories, and existing files, type:

```
compact /c /s
```

To set the compression state of files and subdirectories within the current directory, without altering the compression state of the current directory itself, type:

```
compact /c /s *.*
```

To compress a volume, from the root directory of the volume, type:

```
compact /c /i /s:\
```

Note

This example sets the compression state of all directories (including the root directory on the volume) and compresses every file on the volume. The **/i** parameter prevents error messages from interrupting the compression process.

To compress all files with the .bmp file name extension in the \tmp directory and all subdirectories of \tmp, without modifying the compressed attribute of the directories, type:

```
compact /c /s:\tmp *.bmp
```

To force complete compression of the file *zebra.bmp*, which was partially compressed during a system crash, type:

```
compact /c /f zebra.bmp
```

To remove the compressed attribute from the directory c:\tmp, without changing the compression state of any files in that directory, type:

```
compact /u c:\tmp
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)