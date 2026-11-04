---
layout: Conceptual
title: bitsadmin util and repairservice | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-util-and-repairservice
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin util and repairservice command, which fixes known issues in various versions of BITS service.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 582000ea-64ac-181c-2da3-87c05dc68d1b
document_version_independent_id: 4750d326-dd0d-8b8d-e65a-deb0ed265d63
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-util-and-repairservice.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-util-and-repairservice
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-util-and-repairservice.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 0823ac78-67ab-413a-fa7b-834c5eda3cfc
---

# bitsadmin util and repairservice | Microsoft Learn

If BITS fails to start, this switch attempts to resolve errors related to incorrect service configuration and dependencies on Windows services (such as LANManworkstation) and the network directory. This switch also generates output that indicates if the issues that were resolved.

Note

This command isn't supported by BITS 1.5 and earlier.

## Syntax

```
bitsadmin /util /repairservice [/force]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /force | Optional. Deletes and creates the service again. |

Note

If BITS creates the service again, the service description string might be set to English even in a localized system.

## Examples

To repair the BITS service configuration:

```
bitsadmin /util /repairservice
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin util command](bitsadmin-util)
- [bitsadmin command](bitsadmin)