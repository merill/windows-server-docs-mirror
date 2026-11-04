---
layout: Conceptual
title: fsutil sparse | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-sparse
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil sparse command, which manages sparse files.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 64c6308d-1b60-65df-dbf6-8946affb8c3c
document_version_independent_id: 7aa4cebd-cc83-bcd6-34d8-0e898421ca46
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-sparse.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-sparse
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-sparse.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 383d178a-b87b-67dd-aae1-d1f708f77fac
---

# fsutil sparse | Microsoft Learn

Manages sparse files. A sparse file is a file with one or more regions of unallocated data in it.

A program sees these unallocated regions as containing bytes with a zero value and that there's no disk space representing these zeros. When a sparse file is read, allocated data is returned as stored, and unallocated data is returned, by default, as zeros, in accordance with the C2 security requirement specification. Sparse file support allows data to be deallocated from anywhere in the file.

## Syntax

```
fsutil sparse [queryflag] <filename>
fsutil sparse [queryrange] <filename>
fsutil sparse [setflag] <filename>
fsutil sparse [setrange] <filename> <beginningoffset> <length>
```

### Parameters

| Parameter | Description |
| --- | --- |
| queryflag | Queries sparse. |
| queryrange | Scans a file and searches for ranges that may contain nonzero data. |
| setflag | Marks the indicated file as sparse. |
| setrange | Fills a specified range of a file with zeros. |
| `<filename>` | Specifies the full path to the file including the file name and extension, for example *C:\documents\filename.txt*. |
| `<beginningoffset>` | Specifies the offset within the file to mark as sparse. |
| `<length>` | Specifies the length of the region in the file to be marked as sparse (in bytes). |

#### Remarks

- All meaningful or nonzero data is allocated, whereas all non-meaningful data (large strings of data that is composed of zeros) is not allocated.
- In a sparse file, large ranges of zeroes may not require disk allocation. Space for nonzero data is allocated as needed when the file is written.
- Only compressed or sparse files can have zeroed ranges known to the operating system.
- If the file is sparse or compressed, NTFS may de-allocate disk space within the file. This sets the range of bytes to zeroes without extending the file size.

### Examples

To mark a file named *sample.txt* in the *c:\temp* directory as sparse, type:

```
fsutil sparse setflag c:\temp\sample.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)