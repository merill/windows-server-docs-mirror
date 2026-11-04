---
layout: Conceptual
title: get-DriverPackage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-driverpackage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for get-DriverPackage, which displays information about a driver package on the server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 6a9c702c-4100-8df8-4cb7-ad561c0b6b47
document_version_independent_id: 3ca85901-8413-210e-a5b5-e5651e5a7a6e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-driverpackage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-driverpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-driverpackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 3edaf885-2b4f-407e-109a-212f195a5d72
---

# get-DriverPackage | Microsoft Learn

Displays information about a driver package on the server.

## Syntax

```
wdsutil /Get-DriverPackage [/Server:<Server name>] {/DriverPackage:<Package Name> | /PackageId:<ID>} [/Show:{Drivers | Files | All}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If no server name is specified, the local server is used. |
| [/DriverPackage:&lt;Name&gt;] | Specifies the name of the driver package to show. |
| [/PackageId:&lt;ID&gt;] | Specifies the Windows Deployment Services ID of the driver package to show. You must specify the ID if the driver package cannot be uniquely identified by name. |
| [/Show: {Drivers | Files |

## Examples

To view information about a driver package, type one of the following:

```
wdsutil /Get-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```

```
wdsutil /Get-DriverPackage /DriverPackage:MyDriverPackage /Show:All
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)