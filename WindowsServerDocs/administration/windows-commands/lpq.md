---
layout: Conceptual
title: lpq | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/lpq
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the lpq command, which displays the status of a print queue on a computer running Line printer Daemon (LPD).
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c038b178-f316-07a0-2409-ff83b677349e
document_version_independent_id: 480596b1-8f78-0473-b55c-35324495a3c1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/lpq.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/lpq
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/lpq.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 650787f9-3bb7-0ed0-79d6-15d4bd7f4093
---

# lpq | Microsoft Learn

Displays the status of a print queue on a computer running Line printer Daemon (LPD).

## Syntax

```
lpq -S <servername> -P <printername> [-l]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -S `<servername>` | Specifies (by name or IP address) the computer or printer sharing device that hosts the LPD print queue with a status that you want to display. This parameter is required and must be capitalized. |
| -P `<Printername>` | Specifies (by name) the printer for the print queue with a status that you want to display. This parameter is required and must be capitalized. |
| -l | Specifies that you want to display details about the status of the print queue. |
| /? | Displays help at the command prompt. |

### Examples

To display the status of the *Laserprinter1* printer queue on an LPD host at *10.0.0.45*, type:

```
lpq -S 10.0.0.45 -P Laserprinter1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Print Command Reference](print-command-reference)