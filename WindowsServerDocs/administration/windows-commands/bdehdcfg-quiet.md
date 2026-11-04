---
layout: Conceptual
title: bdehdcfg quiet | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bdehdcfg-quiet
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bdehdcfg quiet command, which tells bdehdcfg to not display all actions and errors.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 2a98bcf5-a625-ab8e-828e-79e6436e4663
document_version_independent_id: 47fdf958-b2fb-a5be-e21a-d96f50fbd5a5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bdehdcfg-quiet.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bdehdcfg-quiet
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bdehdcfg-quiet.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0bc889ee-77f5-6469-80ba-1a1ce564d8b7
---

# bdehdcfg quiet | Microsoft Learn

Informs the bdehdcfg command-line tool that all actions and errors are not to be displayed in the command-line interface. Any Yes/No (Y/N) prompts displayed during the drive preparation will assume a "Yes" answer. To view any error that occurred during drive preparation, review the system event log under the **Microsoft-Windows-BitLocker-DrivePreparationTool** event provider.

## Syntax

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge} -quiet
```

#### Parameters

This command has no additional parameters.

## Examples

To use the **quiet** command:

```
bdehdcfg -target default -quiet
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bdehdcfg](bdehdcfg)