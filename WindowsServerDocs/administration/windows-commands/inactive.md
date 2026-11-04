---
layout: Conceptual
title: inactive | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/inactive
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the inactive command, which marks the system partition or boot partition with focus as inactive on basic master boot record (MBR) disks.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 346eaa63-c019-7d5f-3e78-9e56d2f1022c
document_version_independent_id: a3de95ec-06f5-d654-767f-fa633de9f725
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/inactive.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/inactive
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/inactive.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 4e0fefec-edb9-c060-7809-802956ef67b9
---

# inactive | Microsoft Learn

Marks the system partition or boot partition with focus as inactive on basic master boot record (MBR) disks.

An active system or boot partition must be selected for this operation to succeed. Use the [select partition command](select-partition) command to select the active partition and shift the focus to it.

Caution

Your computer might not start without an active partition. Don't mark a system or boot partition as inactive unless you are an experienced user with a thorough understanding of the Windows family of operating systems.

If you're unable to start your computer after marking the system or boot partition as inactive, insert the Windows Setup CD in the CD-ROM drive, restart the computer, and then repair the partition using the **fixmbr** and **fixboot** commands in the Recovery Console.

After you mark the system partition or boot partition as inactive, your computer starts from the next option specified in the BIOS, such as the CD-ROM drive or a Pre-Boot eXecution Environment (PXE).

## Syntax

```
inactive
```

### Examples

```
inactive
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select partition command](select-partition)
- [Advanced troubleshooting for Windows boot problems](/en-us/windows/client-management/advanced-troubleshooting-boot-problems)