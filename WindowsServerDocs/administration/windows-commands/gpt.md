---
layout: Conceptual
title: gpt | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/gpt
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the gpt command, which assigns the gpt attribute(s) to the partition with focus.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 3270ccf1-3932-c916-beff-2e413a5cb3fb
document_version_independent_id: ad34cd4b-9f77-6f12-9ce2-f03a6a45f5ab
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/gpt.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/gpt
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/gpt.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 2640068d-206f-717e-8581-3df10b2d5cb1
---

# gpt | Microsoft Learn

On basic GUID partition table (gpt) disks, this command assigns the gpt attribute(s) to the partition with focus. Gpt partition attributes give additional information about the use of the partition. Some attributes are specific to the partition type GUID.

You must choose a basic gpt partition for this operation to succeed. Use the [select partition command](select-partition) to select a basic gpt partition and shift the focus to it.

Caution

Changing the gpt attributes might cause your basic data volumes to fail to be assigned drive letters, or to prevent the file system from mounting. We strongly recommend that you don't change the gpt attributes unless you're an original equipment manufacturer (OEM) or an IT professional who's experienced with gpt disks.

## Syntax

```
gpt attributes=<n>
```

### Parameters

| Parameter | Description |
| --- | --- |
| attributes=`<n>` | Specifies the value for the attribute that you want to apply to the partition with focus. The gpt attribute field is a 64-bit field that contains two subfields. The higher field is interpreted only in the context of the partition ID, while the lower field is common to all partition IDs. Accepted values include:<br>- **0x0000000000000001** - Specifies that the partition is required by the computer to function properly.<br>- **0x8000000000000000** - Specifies that the partition won't receive a drive letter by default when the disk is moved to another computer, or when the disk is seen for the first time by a computer.<br>- **0x4000000000000000** - Hides a partition's volume so it's not detected by the mount manager.<br>- **0x2000000000000000** - Specifies that the partition is a shadow copy of another partition.<br>- **0x1000000000000000** - Specifies that the partition is read-only. This attribute prevents the volume from being written to.<br><br><br>For more information about these attributes, see the attributes section at [create_PARTITION_PARAMETERS Structure](/en-us/windows/win32/api/vds/ns-vds-create_partition_parameters). |

#### Remarks

- The EFI System partition contains only those binaries necessary to start the operating system. This makes it easy for OEM binaries or binaries specific to an operating system to be placed in other partitions.

### Examples

To prevent the computer from automatically assigning a drive letter to the partition with focus, while moving a gpt disk, type:

```
gpt attributes=0x8000000000000000
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select partition command](select-partition)
- [create_PARTITION_PARAMETERS Structure](/en-us/windows/win32/api/vds/ns-vds-create_partition_parameters)