---
layout: Conceptual
title: uniqueid | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/uniqueid
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for uniqueid, which displays or sets the GUID partition table (GPT) identifier or master boot record (MBR) signature for the disk with focus.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 055d33b3-3335-f15a-cae0-941ff7936a69
document_version_independent_id: 24fe98c0-0183-69bd-cbb1-245e888f8aa2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/uniqueid.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/uniqueid
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/uniqueid.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bc085828-684c-e674-1132-d2715ec7e353
---

# uniqueid | Microsoft Learn

Displays or sets the GUID partition table (GPT) identifier or master boot record (MBR) signature for the basic or dynamic disk with focus. A basic or dynamic disk must be selected for this operation to succeed. Use the [select disk command](select-disk) to select a disk and shift the focus to it.

## Syntax

```
uniqueid disk [id={<dword> | <GUID>}] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| id=`{<dword> | <GUID>}` | For MBR disks, this parameter specifies a 4-byte (DWORD) value in hexadecimal form for the signature. For GPT disks, this parameter specifies a GUID for the identifier. |
| noerr | For scripting only. When an error occurs, DiskPart continues to process commands as if the error didn't occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To display the signature of the MBR disk with focus, type:

```
uniqueid disk
```

To set the signature of the MBR disk with focus to the DWORD value *5f1b2c36*, type:

```
uniqueid disk id=5f1b2c36
```

To set the identifier of the GPT disk with focus to the GUID value baf784e7-6bbd-4cfb-aaac-e86c96e166ee, type:

```
uniqueid disk id=baf784e7-6bbd-4cfb-aaac-e86c96e166ee
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select disk command](select-disk)