---
layout: Conceptual
title: wdsutil add-imagedriverpackage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-add-imagedriverpackage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil add-imagedriverpackage command, which adds a driver package that is in the driver store to an existing boot image on the server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 23b26eed-edf3-0f3b-42b3-e95462d099f4
document_version_independent_id: 010d59af-bd1d-b69e-39ad-61a1f2d352d2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-add-imagedriverpackage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-add-imagedriverpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-add-imagedriverpackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: fa9643ad-e9f5-a41f-fa7d-c9bb8d018b7f
---

# wdsutil add-imagedriverpackage | Microsoft Learn

Adds a driver package that is in the driver store to an existing boot image on the server.

## Syntax

```
wdsutil /add-ImageDriverPackage [/Server:<Servername>] [media:<Imagename>] [mediatype:Boot] [/Architecture:{x86 | ia64 | x64}] [/Filename:<Filename>] {/DriverPackage:<Package Name> | /PackageId:<ID>}
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:`<Servername>`] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If a server name is not specified, the local server is used. |
| [media:`<Imagename>`] | Specifies the name of the image to add the driver to. |
| [mediatype:Boot] | Specifies the type of image to add the driver to. Driver packages can only be added to boot images. |
| [/Architecture:`{x86 | ia64 | x64}`] | Specifies the architecture of the boot image. Because it's possible to have the same image name for boot images in different architectures, you should specify the architecture to ensure the correct image is used. |
| [/Filename:`<Filename>`] | Specifies the name of the file. If the image cannot be uniquely identified by name, the file name must be specified. |
| [/DriverPackage:`<Name>` | Specifies the name of the driver package to add to the image. |
| [/PackageId:`<ID>`] | Specifies the Windows Deployment Services ID of the driver package. You must specify this option if the driver package can't be uniquely identified by name. To find the Package ID, select the driver group that the package is in (or the **All Packages** node), right-click the package, and then select **Properties**. The Package ID is listed on the **General** tab. For example: {DD098D20-1850-4fc8-8E35-EA24A1BEFF5E}. |

## Examples

To add a driver package to a boot image, type either:

```
wdsutil /add-ImageDriverPackagmedia:WinPE Boot Imagemediatype:Boot /Architecture:x86 /DriverPackage:XYZ
```

```
wdsutil /verbose /add-ImageDriverPackagmedia:WinPE Boot Image /Server:MyWDSServemediatype:Boot /Architecture:x64 /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-imagedriverpackages command](wdsutil-add-imagedriverpackages)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)