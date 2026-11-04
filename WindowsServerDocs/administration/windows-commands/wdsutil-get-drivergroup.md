---
layout: Conceptual
title: wdsutil get-drivergroup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-drivergroup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get-drivergroup, which displays information about the driver groups on a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d43d462c-ab8c-eb0f-d5f2-54127992e7b1
document_version_independent_id: 2b4a390c-0296-6c0f-1142-c37a136b6c70
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-drivergroup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-drivergroup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-drivergroup.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c8e54fb2-ce1d-40c7-4168-bac972c54c7e
---

# wdsutil get-drivergroup | Microsoft Learn

Displays information about the driver groups on a server.

## Syntax

```
wdsutil /Get-DriverGroup /DriverGroup:<Group Name> [/Server:<Server name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /DriverGroup:&lt;Group Name&gt; | Specifies the name of the driver group. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the FQDN. if a server name is not specified, the local server is used. |
| [/Show: {PackageMetaData | Filters | All}] | Displays the metadata for all the driver packages in the specified group. **PackageMetaData** displays information about all the filters for the driver group. **Filters** displays the metadata for all driver packages and filters for the group. |

## Examples

To view information about a driver file, type:

```
wdsutil /Get-DriverGroup /DriverGroup:printerdrivers /Show:PackageMetaData
```

```
wdsutil /Get-DriverGroup /DriverGroup:printerdrivers /Server:MyWdsServer /Show:Filters
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-alldrivergroups command](wdsutil-get-alldrivergroups)