---
layout: Conceptual
title: ver | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ver
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ver command, which displays the operating system version number.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-10-20T00:00:00.0000000Z
locale: en-us
document_id: 04ec5477-2ed5-373e-417d-98536e0a52c5
document_version_independent_id: d352661a-2f30-07b9-b1c9-029483faedfc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ver.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ver
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ver.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 9d363d1e-26f6-5c0d-2ef9-ba9c49cb310f
---

# ver | Microsoft Learn

Displays the operating system version number. This command is supported in the Windows Command prompt (Cmd.exe), but not in any version of PowerShell.

## Syntax

```
ver
```

### Parameters

| Parameter | Description |
| --- | --- |
| /? | Displays help at the command prompt. |

## Examples

To obtain the version number of the operating system from the Command shell (cmd.exe), type:

```
ver
```

If you want to get the operating system version number through Windows PowerShell, type:

```powershell
$PSVersionTable.BuildVersion
```

If you want to get the operating system version number through PowerShell 7.x.x, type:

```powershell
$PSVersionTable.OS
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)