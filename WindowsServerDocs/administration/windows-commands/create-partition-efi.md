---
layout: Conceptual
title: create partition efi | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/create-partition-efi
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the create partition efi command, which creates an Extensible Firmware Interface (EFI) system partition on a GUID Partition Table (gpt) disk on Itanium-based computers.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a874c137-57d2-1613-36f6-10413b2e621c
document_version_independent_id: 35def205-0ece-f6d9-26e9-816d4662b434
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/create-partition-efi.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/create-partition-efi
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/create-partition-efi.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 12f02bb0-d296-5f8a-680a-3913a1b6c110
---

# create partition efi | Microsoft Learn

Creates an Extensible Firmware Interface (EFI) system partition on a GUID Partition Table (gpt) disk on Itanium-based computers. After the partition is created, the focus is given to the new partition.

Note

A gpt disk must be selected for this operation to succeed. Use the [select disk](select-disk) command to select a disk and shift the focus to it.

## Syntax

```
create partition efi [size=<n>] [offset=<n>] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| size=`<n>` | The size of the partition in megabytes (MB). If no size is given, the partition continues until there is no more free space in the current region. |
| offset=`<n>` | The offset in kilobytes (KB), at which the partition is created. If no offset is given, the partition is placed in the first disk extent that is large enough to hold it. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

#### Remarks

- You must add at least one volume with the **add volume** command before you can use the **create** command.
- After you run the **create** command, you can use the **exec** command to run a duplication script for backup from the shadow copy.
- You can use the **begin backup** command to specify a full backup, rather than a copy backup.

## Examples

To create an EFI partition of 1000 megabytes on the selected disk, type:

```
create partition efi size=1000
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [create command](create)
- [select disk](select-disk)