---
layout: Conceptual
title: fsutil clfs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-clfs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the fsutil clfs command.
ms.author: roharwoo
author: robinharwood
ms.topic: reference
ms.date: 2025-03-04T00:00:00.0000000Z
locale: en-us
document_id: bab71d0a-d12d-d274-6d2b-f558e70e6bc5
document_version_independent_id: bab71d0a-d12d-d274-6d2b-f558e70e6bc5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/fsutil-clfs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/fsutil-clfs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/fsutil-clfs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 699ea3b0-87ac-939e-e9ad-ca024f44b36d
---

# fsutil clfs | Microsoft Learn

The `fsutil clfs` command adds authentication support to a Common Log File System (CLFS) logfile that has either invalid or missing authentication codes. Authentication codes are written to the Base Logfile (`.blf`) and all containers associated with the logfile. When authentication is enforced, CLFS opens a logfile if it has valid authentication codes.

## Syntax

```
fsutil clfs authenticate [<BLF Logfile path>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| authenticate | Adds authentication codes to an existing CLFS logfile. |

### Example

The following example adds authentication codes to the "C:\example\_log" logfile:

```
fsutil clfs authenticate "C:\example_log.blf"
```

## Related links

- [Fsutil](fsutil)
- [Introduction to the Common Log File System](/en-us/windows-hardware/drivers/kernel/introduction-to-the-common-log-file-system)
- [Common Log File System API](/en-us/previous-versions/windows/desktop/clfs/common-log-file-system-api)
- [Command-Line Syntax Key](command-line-syntax-key)