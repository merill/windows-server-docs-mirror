---
layout: Conceptual
title: bitsadmin makecustomheaderswriteonly | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-makecustomheaderswriteonly
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin makecustomheaderswriteonly command, which make a job's Custom HTTP Headers write-only.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2019-03-01T00:00:00.0000000Z
locale: en-us
document_id: df0ea389-9972-9153-0376-5a00ef47be85
document_version_independent_id: 4822a5d1-e9d4-b15c-81f2-8f7d155901c9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-makecustomheaderswriteonly.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-makecustomheaderswriteonly
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-makecustomheaderswriteonly.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4a5584dc-87fd-4e63-197d-0e1ec081a122
---

# bitsadmin makecustomheaderswriteonly | Microsoft Learn

Make a job's Custom HTTP Headers write-only.

Important

This action can't be undone.

## Syntax

```
bitsadmin /makecustomheaderswriteonly <job>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |

## Examples

To make Custom HTTP Headers write-only for the job named *myDownloadJob*:

```
bitsadmin /makecustomheaderswriteonly myDownloadJob
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)