---
layout: Conceptual
title: select disk | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/select-disk
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the select disk command, which selects the specified disk and then shifts focus to it.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e621a8a1-0654-0769-a819-f54bd49c2abc
document_version_independent_id: 4534fcbc-15b5-0da3-3313-5d5e83f91f74
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/select-disk.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/select-disk
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/select-disk.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c90d70fa-8231-cfb7-9051-36b115a1dfa3
---

# select disk | Microsoft Learn

Selects the specified disk and shifts the focus to it.

## Syntax

```
select disk={<n>|<disk path>|system|next}
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<n>` | Specifies the number of the disk to receive focus. You can view the numbers for all the disks on the computer by using the **list disk** command in DiskPart.<br>**NOTE**When configuring systems with multiple disks, don't use **select disk=0** to specify the system disk. The computer may reassign disk numbers when you reboot, and different computers with the same disk configuration can have different disk numbers. |
| `<disk path>` | Specifies the location of the disk to receive focus, for example, `PCIROOT(0)#PCI(0F02)#atA(C00T00L00)`. To view the location path of a disk, select it and then type **detail disk**. |
| system | On BIOS computers, this option specifies that disk 0 receives focus. On EFI computers, the disk containing the EFI system partition (ESP), used for the current boot, receives focus. On EFI computers, the command will fail if there's no ESP, if there's more than one ESP, or if the computer is booted from Windows Preinstallation Environment (Windows PE). |
| next | After a disk is selected, this option iterates over all disks in the disk list. When you run this option, the next disk in the list receives focus. |

## Examples

To shift the focus to disk 1, type:

```
select disk=1
```

To select a disk by using its location path, type:

```
select disk=PCIROOT(0)#PCI(0100)#atA(C00T00L01)
```

To shift the focus to the system disk, type:

```
select disk=system
```

To shift the focus to the next disk on the computer, type:

```
select disk=next
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select partition command](select-partition)
- [select vdisk command](select-vdisk)
- [select volume command](select-volume)