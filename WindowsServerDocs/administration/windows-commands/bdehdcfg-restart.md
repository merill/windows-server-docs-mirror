---
layout: Conceptual
title: bdehdcfg restart | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bdehdcfg-restart
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bdehdcfg restart command, which tells bdehdcfg that the computer should be restarted after the drive preparation has concluded.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c5306a27-eb9b-1693-1ee3-4a98946e70d1
document_version_independent_id: a5d1a1e2-8de4-ded8-fb06-24ffc46a0b51
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bdehdcfg-restart.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bdehdcfg-restart
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bdehdcfg-restart.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 07b39889-e10d-2671-6d62-1fcb1cd55e09
---

# bdehdcfg restart | Microsoft Learn

Informs the bdehdcfg command-line tool that the computer should be restarted after the drive preparation has concluded. If other users are logged on to the computer and the **quiet** command is not specified, a prompt appears to confirm that the computer should be restarted.

## Syntax

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge} -restart
```

#### Parameters

This command has no additional parameters.

## Examples

To use the **restart** command:

```
bdehdcfg -target default -restart
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bdehdcfg](bdehdcfg)