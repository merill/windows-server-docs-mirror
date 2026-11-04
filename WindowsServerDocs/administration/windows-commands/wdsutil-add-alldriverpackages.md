---
layout: Conceptual
title: wdsutil add-alldriverpackages | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-add-alldriverpackages
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil add-alldriverpackages command, which adds all driver packages that are stored in a folder to a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 332b30f0-a8dd-8f7e-6ff7-420b83940f92
document_version_independent_id: b7609d72-6759-dbea-bd47-6c7bf97b8a43
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-add-alldriverpackages.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-add-alldriverpackages
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-add-alldriverpackages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7ea77321-72a1-c517-febc-df7b96dc1e66
---

# wdsutil add-alldriverpackages | Microsoft Learn

Adds all driver packages that are stored in a folder to a server.

## Syntax

```
wdsutil /Add-AllDriverPackages /FolderPath:<folderpath> [/Server:<servername>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<groupname>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /FolderPath:`<folderpath>` | Specifies the full path to the folder that contains the .inf files for the driver packages. |
| [/Server:`<servername>`] | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If no server name is specified, the local server is used. |
| [/Architecture:`{x86|ia64|x64}`] | Specifies the architecture type for the driver package. |
| [/DriverGroup:`<groupname>`] | Specifies the name of the driver group to which the packages should be added. |

## Examples

To add driver packages, type either:

```
wdsutil /verbose /Add-AllDriverPackages /FolderPath:C:\Temp\Drivers /Architecture:x86
```

```
wdsutil /Add-AllDriverPackages /FolderPath:C:\Temp\Drivers\Printers /DriverGroup:Printer Drivers
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)
- [Add-WdsDriverPackage](/en-us/powershell/module/wds/add-wdsdriverpackage)