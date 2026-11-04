---
layout: Conceptual
title: attributes volume | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/attributes-volume
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the attributes volume command, which displays, sets, or clears the attributes of a volume.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f1d04f2f-5a63-89cf-cfb1-04402e6ee202
document_version_independent_id: a2123510-6feb-f1c5-5d68-6ee0d3e1fecd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/attributes-volume.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/attributes-volume
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/attributes-volume.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7645ccd5-0f23-fcb5-e71a-e17bab840776
---

# attributes volume | Microsoft Learn

Displays, sets, or clears the attributes of a volume.

## Syntax

```
attributes volume [{set | clear}] [{hidden | readonly | nodefaultdriveletter | shadowcopy}] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| set | Sets the specified attribute of the volume with focus. |
| clear | Clears the specified attribute of the volume with focus. |
| readonly | Specifies that the volume is read-only. |
| hidden | Specifies that the volume is hidden. |
| nodefaultdriveletter | Specifies that the volume does not receive a drive letter by default. |
| shadowcopy | Specifies that the volume is a shadow copy volume. |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

### Remarks

- On basic master boot record (MBR) disks, the **hidden**, **readonly**, and **nodefaultdriveletter** parameters apply to all volumes on the disk.
- On basic GUID partition table (GPT) disks, and on dynamic MBR and gpt disks, the **hidden**, **readonly**, and **nodefaultdriveletter** parameters apply only to the selected volume.
- A volume must be selected for the **attributes volume** command to succeed. Use the **select volume** command to select a volume and shift the focus to it.

## Examples

To display the current attributes on the selected volume, type:

```
attributes volume
```

To set the selected volume as hidden and read-only, type:

```
attributes volume set hidden readonly
```

To remove the hidden and read-only attributes on the selected volume, type:

```
attributes volume clear hidden readonly
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select volume command](select-volume)