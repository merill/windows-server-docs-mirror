---
layout: Conceptual
title: shrink | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/shrink
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the DiskPart shrink command, which reduces the size of the selected volume by the amount you specify.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 32f07b12-f782-6441-bdae-cf5707f1573f
document_version_independent_id: 29172f7b-ca1e-0b76-75c7-4cb400f37afc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/shrink.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/shrink
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/shrink.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: daf05dd7-532a-8e71-1e07-8d455d4d1424
---

# shrink | Microsoft Learn

The Diskpart shrink command reduces the size of the selected volume by the amount you specify. This command makes free disk space available from the unused space at the end of the volume.

A volume must be selected for this operation to succeed. Use the **select volume** command to select a volume and shift the focus to it.

Note

This command works on basic volumes, and on simple or spanned dynamic volumes. It doesn't work on original equipment manufacturer (OEM) partitions, Extensible Firmware Interface (EFI) system partitions, or recovery partitions.

## Syntax

```
shrink [desired=<n>] [minimum=<n>] [nowait] [noerr]
shrink querymax [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| desired=`<n>` | Specifies the desired amount of space in megabytes (MB) to reduce the size of the volume by. |
| minimum=`<n>` | Specifies the minimum amount of space in MB to reduce the size of the volume by. |
| querymax | Returns the maximum amount of space in MB by which the volume can be reduced. This value may change if applications are currently accessing the volume. |
| nowait | Forces the command to return immediately while the shrink process is still in progress. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

#### Remarks

- You can reduce the size of a volume only if it is formatted using the NTFS file system or if it does not have a file system.
- If a desired amount isn't specified, the volume is reduced by the minimum amount (if specified).
- If a minimum amount isn't specified, the volume is reduced by the desired amount (if specified).
- If neither a minimum amount nor a desired amount is specified, the volume is reduced by as much as possible.
- If a minimum amount is specified, but not enough free space is available, the command fails.

## Examples

To reduce the size of the selected volume by the largest possible amount between 250 and 500 megabytes, type:

```
shrink desired=500 minimum=250
```

To display the maximum number of MB that the volume can be reduced by, type:

```
shrink querymax
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Resize-Partition](/en-us/powershell/module/storage/resize-partition?view=win10-ps&amp;preserve-view=true)