---
layout: Conceptual
title: online disk | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/online-disk
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the online disk command, which takes the offline disk to the online state.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b2588e07-d7bd-f284-d177-17345c0d2cef
document_version_independent_id: 22e99760-a118-31b9-96a7-b64ce39a120a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/online-disk.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/online-disk
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/online-disk.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8f4c5779-a00f-8c5f-5c79-c132bd1d7fa2
---

# online disk | Microsoft Learn

Takes the offline disk to the online state. For basic disks, this command attempts to bring online the selected disk and all volumes on that disk. For dynamic disks, this command attempts to bring online all disks that are not marked as foreign on the local computer. It also attempts to bring online all volumes on the set of dynamic disks.

If a dynamic disk in a disk group is brought online and it's the only disk in the group, then the original group is recreated and the disk is moved to that group. If there are other disks in the group and they're online, then the disk is simply added back into the group. If the group of a selected disk contains mirrored or RAID-5 volumes, this command also resynchronizes these volumes.

Note

A disk must be selected for the **online disk** command to succeed. Use the [select disk](select-disk) command to select a disk and shift the focus to it.

Important

This command will fails if it's used on a read-only disk.

## Syntax

```
online disk [noerr]
```

### Parameters

For instructions about using this command, see [Reactivate a Missing or Offline Dynamic Disk](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc732026%28v=ws.11%29).

| Parameter | Description |
| --- | --- |
| noerr | For scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

### Examples

To take the disk with focus online, type:

```
online disk
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)