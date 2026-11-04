---
layout: Conceptual
title: break | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/break
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the break command, which breaks the mirrored volume with focus into two simple volumes.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: fc995a12-c47c-715c-9050-dd38bc621ec5
document_version_independent_id: e4f947c4-fa5d-5a4a-ee2b-7d008ebbc8d9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/break.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/break
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/break.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 29bb1804-6128-2d41-53bf-2c3d142cb448
---

# break | Microsoft Learn

Important

This command is no longer in use. It is included only to preserve compatibility with existing MS-DOS files, but it has no effect at the command line because the functionality is automatic.

Sets or clears extended CTRL+C checking on MS-DOS systems. If used without parameters, **break** displays the existing setting value.

If command extensions are enabled and running on the Windows platform, inserting the **break** command into a batch file enters a hard-coded breakpoint if being debugged by a debugger.

## Syntax

```
break=[on|off]
```

Note

Because the break command has no effect, it is often used to create empty files or delete the content of an existing file. For example:

```
rem -- cleans the content of the file --
break>log
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [break command](break)