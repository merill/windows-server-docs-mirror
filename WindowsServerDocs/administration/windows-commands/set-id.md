---
layout: Conceptual
title: set id | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/set-id
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the Diskpart set id command, which changes the partition type field for the partition with focus.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f6360c07-3448-8cff-b09f-5336115c7f97
document_version_independent_id: e9163602-9e84-3dfe-1e42-8f2382449f16
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/set-id.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/set-id
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/set-id.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 097b3362-324d-3170-66ec-6a30b5c34a13
---

# set id | Microsoft Learn

Changes the partition type field for the partition with focus. This command doesn't work on dynamic disks or on Microsoft Reserved partitions.

Important

This command is intended for use by original equipment manufacturers (OEMs) only. Changing partition type fields with this parameter might cause your computer to fail or be unable to boot. Unless you are an OEM or experienced with gpt disks, you should not change partition type fields on gpt disks by using this parameter. Instead, always use the [create partition efi](create-partition-efi) command to create EFI system partitions, the [create partition msr](create-partition-msr) command to create Microsoft Reserved partitions, and the [create partition primary](create-partition-primary) command without the ID parameter to create primary partitions on gpt disks.

## Syntax

```
set id={ <byte> | <GUID> } [override] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<byte>` | For master boot record (MBR) disks, specifies the new value for the type field, in hexadecimal form, for the partition. Any partition type **byte** can be specified with this parameter except for type 0x42, which specifies an LDM partition. Note that the leading 0x is omitted when specifying the hexadecimal partition type. |
| `<GUID>` | For GUID partition table (gpt) disks, specifies the new GUID value for the type field for the partition. Recognized GUIDs include:<br>- **EFI system partition:** c12a7328-f81f-11d2-ba4b-00a0c93ec93b<br>- **Basic data partition:** ebd0a0a2-b9e5-4433-87c0-68b6b72699c7<br><br>Any partition type GUID can be specified with this parameter except the following:<br>- **Microsoft Reserved partition:** e3c9e316-0b5c-4db8-817d-f92df00215ae<br>- **LDM metadata partition on a dynamic disk:** 5808c8aa-7e8f-42e0-85d2-e1e90434cfb3<br>- **LDM data partition on a dynamic disk:** af9b60a0-1431-4f62-bc68-3311714a69ad<br>- **Cluster metadata partition:** db97dba9-0840-4bae-97f0-ffb9a327c7e1 |
| override | forces the file system on the volume to dismount before changing the partition type. When you run the **set id** command, DiskPart attempts to lock and dismount the file system on the volume. If **override** isn't specified, and the call to lock the file system fails (for example, because there is an open handle), the operation fails. If **override** is specified, DiskPart forces the dismount even if the call to lock the file system fails, and any open handles to the volume will stop being valid. |
| noerr | Used for scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Remarks

- Other than the limitations previously mentioned, DiskPart doesn't check the validity of the value that you specify (except to ensure that it is a byte in hexadecimal form or a GUID).

## Examples

To set the type field to *0x07* and force the file system to dismount, type:

```
set id=0x07 override
```

To set the type field to be a basic data partition, type:

```
set id=ebd0a0a2-b9e5-4433-87c0-68b6b72699c7
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)