---
layout: Conceptual
title: add-DriverPackage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-add-driverpackage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the add-DriverPackage command, which adds a driver package to the server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c85a8075-9416-a474-0f16-1e5d325fb70c
document_version_independent_id: dc62475e-166c-6e7c-7e7d-b3336515bfd9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-add-driverpackage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-add-driverpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-add-driverpackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 1682a2c1-1405-0995-5f1d-0d6f1c2dcd2f
---

# add-DriverPackage | Microsoft Learn

Adds a driver package to the server.

## Syntax

```
wdsutil /Add-DriverPackage /InfFile:<Inf File path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>] [/Name:<Friendly Name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /InfFile:`<InfFilepath>` | Specifies the full path of the .inf file to add. |
| [/Server:`<Servername>`] | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If no server name is specified, the local server is used. |
| [/Architecture:`{x86 | ia64 | x64}`] | Specifies the architecture type for the driver package. |
| [/DriverGroup:`<groupname>`] | Specifies the name of the driver group to which the packages should be added. |
| [/Name:`<friendlyname>`] | Specifies the friendly name for the driver package. |

## Examples

To add a driver package, type either:

```
wdsutil /verbose /Add-DriverPackage /InfFile:C:\Temp\Display.inf
```

```
wdsutil /Add-DriverPackage /Server:MyWDSServer /InfFile:C:\Temp\Display.inf /Architecture:x86 /DriverGroup:x86Drivers /Name:Display Driver
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-drivergrouppackage command](wdsutil-add-drivergrouppackage)
- [wdsutil add-alldriverpackages command](wdsutil-add-alldriverpackages)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)