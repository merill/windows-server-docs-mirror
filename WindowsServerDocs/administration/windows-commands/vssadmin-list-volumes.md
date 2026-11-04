---
layout: Conceptual
title: vssadmin list volumes - in Windows and Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/vssadmin-list-volumes
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: vssadmin list volumes shows all volumes that are eligible for shadow copies. Learn the command syntax and find related Windows commands.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2026-09-07T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: b13f474a-0ffa-1a5d-f81e-bb5f2c35c91e
document_version_independent_id: b13f474a-0ffa-1a5d-f81e-bb5f2c35c91e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/vssadmin-list-volumes.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/vssadmin-list-volumes
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/vssadmin-list-volumes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: a18cba45-6f87-bc08-5112-20b83acedc22
---

# vssadmin list volumes - in Windows and Windows Server | Microsoft Learn

The `vssadmin list volumes` command shows all volumes that are eligible for shadow copies. Use this command to identify which volumes you can shadow copy before you create or configure one.

## Syntax

```
vssadmin list volumes
```

## Examples

To list all volumes that are eligible for shadow copies, type:

```
vssadmin list volumes
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [vssadmin command](vssadmin)