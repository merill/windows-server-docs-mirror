---
layout: Conceptual
title: netsh show | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-show
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh show command displays the alias and DLL helper modules available within the netsh in Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-29T00:00:00.0000000Z
locale: en-us
document_id: c6dac73e-2c9b-5342-add5-44ccdfc4580e
document_version_independent_id: c6dac73e-2c9b-5342-add5-44ccdfc4580e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-show.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-show
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-show.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 2409c3eb-d5dc-7d6d-f154-1c92317b2fcf
---

# netsh show | Microsoft Learn

The `netsh show` command displays information about defined command aliases and available dynamic link library (DLL) modules.

## Syntax

```
netsh show <alias> <helper>
```

## Parameters

| Parameter | Description |
| --- | --- |
| `alias` | Lists all the defined aliases in the `netsh` context. Aliases are shortcuts that can be created for longer commands or sequences. |
| `helper` | Lists all the top-level DLL helpers available. |

## Examples

To see the aliases used within your environment, run the following command:

```cmd
netsh show alias
```

To see a list of the DLL helper files used within your environment, run the following command:

```cmd
netsh show helper
```