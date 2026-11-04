---
layout: Conceptual
title: bitsadmin monitor | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-monitor
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin monitor command, which monitors jobs in the transfer queue that are owned by the current user.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a94bb541-3fde-d53a-0c21-e1bafd56c76a
document_version_independent_id: 996d1f3c-693d-ef55-9e9d-90ac3818197c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-monitor.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-monitor
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-monitor.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 6678c3d9-84ea-d7a8-1833-324e5faa1265
---

# bitsadmin monitor | Microsoft Learn

Monitors jobs in the transfer queue that are owned by the current user.

## Syntax

```
bitsadmin /monitor [/allusers] [/refresh <seconds>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /allusers | Optional. Monitors jobs for all users. You must have administrator privileges to use this parameter. |
| /refresh | Optional. Refreshes the data at an interval specified by `<seconds>`. The default refresh interval is five seconds. To stop the refresh, press CTRL+C. |

## Examples

To monitor the transfer queue for jobs owned by the current user and refreshes the information every 60 seconds.

```
bitsadmin /monitor /refresh 60
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)