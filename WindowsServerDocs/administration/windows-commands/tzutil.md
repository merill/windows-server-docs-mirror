---
layout: Conceptual
title: tzutil | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tzutil
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tzutil command, which displays the Windows Time Zone utility.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a1c0add1-f2b7-9eb9-5f16-350e94a191e4
document_version_independent_id: 19261da7-d370-e21d-dccb-6608f60338f2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tzutil.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tzutil
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tzutil.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 9edba9ea-e53b-9c45-923f-412984647fd2
---

# tzutil | Microsoft Learn

Displays the Windows Time Zone utility.

## Syntax

```
tzutil [/?] [/g] [/s <timezoneID>[_dstoff]] [/l]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /g | Displays the current time zone ID. |
| /s `<timezoneID>[_dstoff]` | Sets the current time zone using the specified time zone ID. The **\_dstoff** suffix disables Daylight Saving time adjustments for the time zone (where applicable). Your value must be surrounded by quotes. |
| /l | Lists all valid time zone IDs and display names. The output appears as:<br>- `<display name>`<br>- `<time zone ID>` |
| /? | Displays help at the command prompt. |

#### Remarks

An exit code of **0** indicates the command completed successfully.

## Examples

To display the current time zone ID, type:

```
tzutil /g
```

To set the current time zone to Pacific Standard time, type:

```
tzutil /s "Pacific Standard time"
```

To set the current time zone to Pacific Standard time and disable Daylight Saving time adjustments, type:

```
tzutil /s "Pacific Standard time_dstoff"
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)