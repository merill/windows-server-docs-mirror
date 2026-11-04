---
layout: Conceptual
title: verify | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/verify
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the verify command, which tells the Command Prompt tool whether to verify your files are written correctly to a disk.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-11-01T00:00:00.0000000Z
locale: en-us
document_id: 75156a43-c17c-fcfd-6304-488cb08dfd13
document_version_independent_id: 26bb219d-4fa7-a2e4-4b6e-220e47101b88
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/verify.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/verify
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/verify.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d7f93ac1-f119-9e53-7b16-8e8563429489
---

# verify | Microsoft Learn

Tells the Command Prompt tool (cmd.exe) whether to verify your files are written correctly to a disk.

## Syntax

```
verify [on | off]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[on \| off]` | Switches the **verify** setting on or off. |
| /? | Displays help at the command prompt. |

## Examples

To display the current **verify** setting, type:

```
verify
```

To turn the **verify** setting on, type:

```
verify on
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)