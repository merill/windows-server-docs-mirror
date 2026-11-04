---
layout: Conceptual
title: bdehdcfg newdriveletter | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bdehdcfg-newdriveletter
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bdehdcfg newdriveletter command, which assigns a new drive letter to the portion of a drive used as the system drive.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1d5e2f4e-7241-188f-ae82-fed43eb07fa1
document_version_independent_id: 2e6c0a51-65fa-4e3e-d0ca-73e83838aa5c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bdehdcfg-newdriveletter.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bdehdcfg-newdriveletter
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bdehdcfg-newdriveletter.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c00b8344-7b51-c2e1-b6ff-b6be4f70d35f
---

# bdehdcfg newdriveletter | Microsoft Learn

Assigns a new drive letter to the portion of a drive used as the system drive. As a best practice, we recommend not assigning a drive letter to your system drive.

## Syntax

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge} -newdriveletter <drive_letter>
```

#### Parameters

| Parameter | Description |
| --- | --- |
| `<drive_letter>` | Defines the drive letter that will be assigned to the specified target drive. |

## Examples

To assign the default drive the drive letter `P`:

```
bdehdcfg -target default -newdriveletter P:
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bdehdcfg](bdehdcfg)