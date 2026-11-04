---
layout: Conceptual
title: perfmon | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/perfmon
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the perfmon command, which starts the Windows Reliability and Performance Monitor in a specific standalone mode.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-25T00:00:00.0000000Z
locale: en-us
document_id: 2965254e-56e1-da6a-879f-f0b7571f1e57
document_version_independent_id: 4287349e-d78d-3d92-1d9f-494217c2be5e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/perfmon.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/perfmon
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/perfmon.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ea374467-4cbc-5af6-11d0-f10742096889
---

# perfmon | Microsoft Learn

Start Windows Reliability and Performance Monitor in a specific standalone mode.

## Syntax

```
perfmon </res|report|rel|sys>
```

### Parameters

| Parameter | Description |
| --- | --- |
| /res | Starts the Resource View. |
| /report | Starts the System Diagnostics Data Collector Set and displays a report of the results. |
| /rel | Starts the Reliability Monitor. |
| /sys | Starts the Performance Monitor. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Windows Performance Monitor](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc749154%28v%3dws.11%29)