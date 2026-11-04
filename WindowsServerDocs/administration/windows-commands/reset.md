---
layout: Conceptual
title: reset | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reset
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the reset command, which resets DiskShadow.exe to the default state.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 2c26bae8-e7f5-597d-be01-5031228a1a38
document_version_independent_id: 14f0182c-148a-a4a2-c5e5-4c3f9db618e2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reset.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reset
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reset.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: 05ce9b03-c47d-8542-897f-7c5e207d2e20
---

# reset | Microsoft Learn

Resets DiskShadow.exe to the default state. This command is especially useful in separating compound DiskShadow operations, such as **create**, **import**, **backup**, or **restore**.

> 
> [!IMPORTANT After you run this command, you will lose state information from commands, such as **add**, **set**, **load**, or **writer**. This command also releases IVssBackupComponent interfaces and loses non-persistent shadow copies.

## Syntax

```
reset
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [create command](create)
- [import command](import_1)
- [backup command](begin-backup)
- [restore command](begin-restore)
- [add command](add)
- [set command](set)
- [load command](reg-load)
- [writer command](writer)