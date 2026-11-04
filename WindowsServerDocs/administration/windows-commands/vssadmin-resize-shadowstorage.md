---
layout: Conceptual
title: vssadmin resize shadowstorage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/vssadmin-resize-shadowstorage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: A description of the vssadmin resize shadowstorage command, which resizes the maximum amount of storage space that can be used for shadow copy storage.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2020-03-05T00:00:00.0000000Z
locale: en-us
document_id: 1304ffe7-7467-5af3-f282-b519619dd1eb
document_version_independent_id: f95d24ed-b716-f036-b35a-3cf96283f7da
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/vssadmin-resize-shadowstorage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/vssadmin-resize-shadowstorage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/vssadmin-resize-shadowstorage.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ea70b17c-11c5-39ca-7898-74e5d04e5b00
---

# vssadmin resize shadowstorage | Microsoft Learn

Resizes the maximum amount of storage space that can be used for shadow copy storage.

The minimum amount of storage space that can be used for shadow copy storage can be specified by using the **MinDiffAreaFileSize** registry value. For more information, see [MinDiffAreaFileSize](/en-us/windows/win32/backup/registry-keys-for-backup-and-restore#mindiffareafilesize).

Warning

Resizing the storage association may cause shadow copies to disappear.

## Syntax

```
vssadmin resize shadowstorage /for=<ForVolumeSpec> /on=<OnVolumeSpec> [/maxsize=<MaxSizeSpec>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /for=`<ForVolumeSpec>` | Specifies the volume for which the maximum amount of storage space is to be resized. |
| /on=`<OnVolumeSpec>` | Specifies the storage volume. |
| [/maxsize=`<MaxSizeSpec>`] | Specifies the maximum amount of space that can be used for storing shadow copies. If no value is specified for **/maxsize**, there's no limit placed on the amount of storage space that can be used.<br>The **MaxSizeSpec** value must be 1 MB or greater and must be expressed in one of the following units: KB, MB, GB, TB, PB, or EB. If no unit is specified, **MaxSizeSpec** uses bytes by default. |

## Examples

To resize shadow copy of volume C on volume D, with a maximum size of 900MB, type:

```
vssadmin resize shadowstorage /For=C: /On=D: /MaxSize=900MB
```

To resize shadow copy of volume C on volume D, with no maximum size, type:

```
vssadmin resize shadowstorage /For=C: /On=D: /MaxSize=UNBOUNDED
```

To resize shadow copy of volume C by 20%, type:

```
vssadmin resize shadowstorage /For=C: /On=C: /MaxSize=20%
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [vssadmin command](vssadmin)