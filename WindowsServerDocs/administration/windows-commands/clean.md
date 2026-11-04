---
layout: Conceptual
title: clean | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/clean
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the Diskpart clean command, which removes all partitions or volume formatting from the disk with focus.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 96a39faf-885a-39f1-28d2-0a6b2541b865
document_version_independent_id: 6330e3d8-5504-d10b-9a4c-22e5ba859031
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/clean.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/clean
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/clean.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 832189cc-8258-533e-2a70-3cf78160edae
---

# clean | Microsoft Learn

Removes all partitions or volume formatting from the disk with focus.

Note

For a PowerShell version of this command, see [clear-disk command](/en-us/powershell/module/storage/clear-disk).

## Syntax

```
clean [all]
```

### Parameters

| Parameter | Description |
| --- | --- |
| all | Specifies that each and every sector on the disk is set to zero, which completely deletes all data contained on the disk. |

#### Remarks

- On master boot record (MBR) disks, only the MBR partitioning information and hidden sector information is overwritten.
- On GUID Partition Table (gpt) disks, the gpt partitioning information, including the Protective MBR, is overwritten. There is no hidden sector information.
- A disk must be selected for this operation to succeed. Use the **select disk** command to select a disk and shift the focus to it.

## Examples

To remove all formatting from the selected disk, type:

```
clean
```

## Related links

- [clear-disk command](/en-us/powershell/module/storage/clear-disk)
- [Command-Line Syntax Key](command-line-syntax-key)