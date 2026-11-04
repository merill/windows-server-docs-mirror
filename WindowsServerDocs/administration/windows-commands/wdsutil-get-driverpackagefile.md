---
layout: Conceptual
title: wdsutil get-driverpackagefile | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-driverpackagefile
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get-driverpackagefile, which displays information about a driver package, including the drivers and files it contains.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2024-08-19T00:00:00.0000000Z
locale: en-us
document_id: 33e1347e-27ce-4cf3-12ad-2731572c4a43
document_version_independent_id: f218dd86-1529-9421-1b9a-43767c036389
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-driverpackagefile.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-driverpackagefile
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-driverpackagefile.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a885086f-a452-05ff-b9f1-00a8f3dbdded
---

# wdsutil get-driverpackagefile | Microsoft Learn

Displays information about a driver package, including the drivers and files it contains.

## Syntax

```
wdsutil /Get-DriverPackageFile /InfFile:<InfFilePath> [/Architecture:{x86 | x64 | arm | arm64}] [/Show:{Drivers | Files | All}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /InfFile:`<InfFilePath>` | Specifies the full path and file name of the driver package `.inf` file. |
| /Architecture:`x86 | x64 | arm | arm64` | The architecture of the driver package. |
| /Show:`Drivers | Files | All` | Indicates the package information to display. The default, if `/show` isn't specified, is to return only the driver package metadata. <br>- **Drivers** displays the list of drivers in the package.<br>- **Files** displays the list of files in the package.<br>- **All** displays drivers and files. |

## Examples

To view information about a driver file, type:

```
wdsutil /Get-DriverPackageFile /InfFile:C:\temp\1394.inf /Architecture:x86
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)