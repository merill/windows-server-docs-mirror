---
layout: Conceptual
title: fsutil quota | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-quota
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil quota command, which manages disk quotas on NTFS volumes to provide more precise control of network-based storage.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f2d140e3-5d31-e76a-7f3a-725e2f07c756
document_version_independent_id: 88f1553b-1a3f-0b80-2180-adfeac3bb2ba
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-quota.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-quota
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-quota.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 882c4d16-70e8-d953-4b91-0620e4c9b409
---

# fsutil quota | Microsoft Learn

Manages disk quotas on NTFS volumes to provide more precise control of network-based storage.

## Syntax

```
fsutil quota [disable] <volumepath>
fsutil quota [enforce] <volumepath>
fsutil quota [modify] <volumepath> <threshold> <limit> <username>
fsutil quota [query] <volumepath>
fsutil quota [track] <volumepath>
fsutil quota [violations]
```

### Parameters

| Parameter | Description |
| --- | --- |
| disable | Disables quota tracking and enforcement on the specified volume. |
| enforce | Enforces quota usage on the specified volume. |
| modify | Modifies an existing disk quota or creates a new quota. |
| query | Lists existing disk quotas. |
| track | Tracks disk usage on the specified volume. |
| violations | Searches the system and application logs and displays a message to indicate that quota violations have been detected or that a user has reached a quota threshold or quota limit. |
| `<volumepath>` | Required. Specifies the drive name followed by a colon or the GUID in the format `volume{GUID}`. |
| `<threshold>` | Sets the limit (in bytes) at which warnings are issued. This parameter is required for the `fsutil quota modify` command. |
| `<limit>` | Sets the maximum allowed disk usage (in bytes). This parameter is required for the `fsutil quota modify` command. |
| `<username>` | Specifies the domain or user name. This parameter is required for the `fsutil quota modify` command. |

#### Remarks

- Disk quotas are implemented on a per-volume basis, and they enable both hard and soft storage limits to be implemented on a per-user basis.
- You can use write scripts that use **fsutil quota** to set the quota limits every time you add a new user or to automatically track quota limits, compile them into a report, and automatically send them to the system administrator in e-mail.

### Examples

To list existing disk quotas for a disk volume that is specified with the GUID, {928842df-5a01-11de-a85c-806e6f6e6963}, type:

```
fsutil quota query volume{928842df-5a01-11de-a85c-806e6f6e6963}
```

To list existing disk quotas for a disk volume that is specified with the drive letter, **C:**, type:

```
fsutil quota query C:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [fsutil](fsutil)