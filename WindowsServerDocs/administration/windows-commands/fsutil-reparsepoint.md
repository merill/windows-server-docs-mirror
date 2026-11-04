---
layout: Conceptual
title: fsutil reparsepoint | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-reparsepoint
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil reparsepoint command, which queries or deletes reparse points.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f84c7464-e04f-1015-54a3-4c1bc428ecfa
document_version_independent_id: a371b1cd-19a8-4f22-3f9e-90b3ef227e7f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-reparsepoint.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-reparsepoint
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-reparsepoint.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c3df71ad-ef9d-8aa1-f0fc-45602c979650
---

# fsutil reparsepoint | Microsoft Learn

Queries or deletes reparse points. The **fsutil reparsepoint** command is typically used by support professionals.

Reparse points are NTFS file system objects that have a definable attribute, which contains user-defined data. They're used to:

- Extend functionality in the input/output (I/O) subsystem.
- Act as directory junction points and volume mount points.
- Mark certain files as special to a file system filter driver.

## Syntax

```
fsutil reparsepoint [query] <filename>
fsutil reparsepoint [delete] <filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| query | Retrieves the reparse point data that is associated with the file or directory identified by the specified handle. |
| delete | Deletes a reparse point from the file or directory that is identified by the specified handle, but does not delete the file or directory. |
| `<filename>` | Specifies the full path to the file including the file name and extension, for example *C:\documents\filename.txt*. |

#### Remarks

- When a program sets a reparse point, it stores this data, plus a reparse tag, which uniquely identifies the data it is storing. When the file system opens a file with a reparse point, it attempts to find the associated file system filter. If the file system filter is found, the filter processes the file as directed by the reparse data. If no file system filter is found, the **File open** operation fails.

### Examples

To retrieve reparse point data associated with *c:\server*, type:

```
fsutil reparsepoint query c:\server
```

To delete a reparse point from a specified file or directory, use the following format:

```
fsutil reparsepoint delete c:\server
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)