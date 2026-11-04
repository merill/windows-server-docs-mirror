---
layout: Conceptual
title: bdehdcfg driveinfo | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bdehdcfg-driveinfo
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bdehdcfg driveinfo command, which displays the drive letter, the total size, the maximum free space, and the partition characteristics.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7d85f49d-2995-9b5a-83ee-520e105a5581
document_version_independent_id: f8bfdeae-42cf-0ed7-3b94-b8016f1523b5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bdehdcfg-driveinfo.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bdehdcfg-driveinfo
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bdehdcfg-driveinfo.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d4b6f17e-ecf2-7278-5a0b-3e9339587b22
---

# bdehdcfg driveinfo | Microsoft Learn

Displays the drive letter, the total size, the maximum free space, and the partition characteristics. Only valid partitions are listed. Unallocated space is not listed if four primary or extended partitions already exist.

Note

This command is informational only and makes no changes to the drive.

## Syntax

```
bdehdcfg -driveinfo <drive_letter>
```

### Parameters

| Parameter | Description |
| --- | --- |
| &lt;drive\_letter&gt; | Specifies a drive letter followed by a colon. |

## Example

To display the drive information for the C: drive:

```
bdehdcfg -driveinfo C:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bdehdcfg](bdehdcfg)