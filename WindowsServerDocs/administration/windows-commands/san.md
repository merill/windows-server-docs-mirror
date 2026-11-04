---
layout: Conceptual
title: san | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/san
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the san command that displays or sets the storage area network (SAN) policy for the operating system.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-04-01T00:00:00.0000000Z
locale: en-us
document_id: 7edff16f-948d-6381-7431-acb48bdb05c7
document_version_independent_id: f062f74b-6512-727f-c2c2-d3df63e0f9d4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/san.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/san
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/san.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/062d60c9-ee0f-402e-a046-b4e67c3572d6
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/17d3b3f6-a66e-4c69-9774-14a73c38e669
platformId: e3795c5d-fae7-0abc-9e20-9c245f9c7c32
---

# san | Microsoft Learn

Displays or sets the storage area network (san) policy for the operating system. If used without parameters, the current san policy is displayed.

## Syntax

```
san [policy={onlineAll | offlineAll | offlineShared}] [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| policy={onlineAll|offlineAll|offlineShared}] | Sets the san policy for the currently booted operating system. The san policy determines whether a newly discovered disk is brought online or remains offline, and whether it becomes read/write or remains read-only. When a disk is offline, the disk layout can be read, but no volume devices are surfaced through Plug and Play. When offline no file system can be mounted on the disk. When a disk is online, one or more volume devices are installed for the disk. The following parameter can be set:<br>- **onlineAll**. Specifies that all newly discovered disks are online and made read/write. **IMPORTANT:** Specifying **onlineAll** on a server that shares disks could lead to data corruption. Therefore, you shouldn't set this policy if disks are shared among servers unless the server is part of a cluster.<br>- **offlineAll**. Specifies that all newly discovered disks except the startup disk are offline and read-only by default.<br>- **offlineShared**. Specifies that all newly discovered disks that don't reside on a shared bus (such as SCSI and iSCSI) are brought online and made read-write. Disks that are left offline are read-only by default.<br><br>For more information, see [VDS_san_POLICY Enumeration](/en-us/windows/win32/api/vds/ne-vds-vds_san_policy). |
| noerr | Used for scripting only. When an error is encountered, DiskPart continues to process commands as if the error didn't occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To view the current policy, type:

```
san
```

To make all newly discovered disks, except the startup disk, offline and read-only by default, type:

```
san policy=offlineAll
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)