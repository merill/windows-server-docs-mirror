---
layout: Conceptual
title: wdsutil get-alldrivergroups | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-alldrivergroups
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil get-alldrivergroups command, which displays information about all the driver groups on a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c21d5f96-64e2-a863-5ad4-0549a8035815
document_version_independent_id: 0356f8b5-dbbd-8333-44ed-c6500a82b66d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-alldrivergroups.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-alldrivergroups
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-alldrivergroups.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3183b73e-d7a8-9842-e3f6-a759d383c094
---

# wdsutil get-alldrivergroups | Microsoft Learn

Displays information about all the driver groups on a server.

## Syntax

```
wdsutil /get-alldrivergroups [/server:<servername>] [/show:{packagemetadata | filters | all}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[/server:<servername>]` | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If a server name is not specified, the local server is used. |
| `/show:{packagemetadata | filters | all}]` | Displays the metadata for all the driver packages in the specified group. **PackageMetaData** displays information about all the filters for the driver group. **Filters** displays the metadata for all driver packages and filters for the group. |

## Examples

To view information about a driver file, type either:

```
wdsutil /get-alldrivergroups /server:MyWdsServer /show:All
```

```
wdsutil /get-alldrivergroups [/show:packagemetadata]
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-drivergroup command](wdsutil-get-drivergroup)