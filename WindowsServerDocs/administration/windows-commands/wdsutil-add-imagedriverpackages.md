---
layout: Conceptual
title: wdsutil add-imagedriverpackages | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-add-imagedriverpackages
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil add-imagedriverpackages command, which adds driver packages from the driver store to a boot image.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a15d98c5-cdec-007e-a3f1-44738460c13b
document_version_independent_id: d6b01b78-874c-7df2-7a78-539e44718f94
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-add-imagedriverpackages.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-add-imagedriverpackages
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-add-imagedriverpackages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 828d273d-df83-21a2-5821-cbd3f6a92d29
---

# wdsutil add-imagedriverpackages | Microsoft Learn

Adds driver packages from the driver store to a boot image.

## Syntax

```
wdsutil /add-ImageDriverPackages [/Server:<Server name>media:<Image namemediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>] /Filtertype:<Filter type> /Operator:{Equal | NotEqual | GreaterOrEqual | LessOrEqual | Contains} /Value:<Value> [/Value:<Value> ...]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:`<Servername>`] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If a server name is not specified, the local server is used. |
| [media:`<Imagename>`] | Specifies the name of the image to add the driver to. |
| [mediatype:Boot] | Specifies the type of image to add the driver to. Driver packages can only be added to boot images. |
| [/Architecture:`{x86 | ia64 | x64}`] | Specifies the architecture of the boot image. Because it's possible to have the same image name for boot images in different architectures, you should specify the architecture to ensure the correct image is used. |
| [/Filename:`<Filename>`] | Specifies the name of the file. If the image cannot be uniquely identified by name, the file name must be specified. |
| /Filtertype:`<Filtertype>` | Specifies the attribute of the driver package to search for. You can specify multiple attributes in a single command. You must also specify **/Operator** and **/Value** with this option. Valid values include:<br>- PackageId<br>- PackageName<br>- PackageEnabled<br>- Packagedateadded<br>- PackageInfFilename<br>- PackageClass<br>    PackageProvider<br>- PackageArchitecture<br>- PackageLocale<br>- PackageSigned<br>- PackagedatePublished<br>- Packageversion<br>- Driverdescription<br>- DriverManufacturer<br>- DriverHardwareId<br>- DrivercompatibleId<br>- DriverExcludeId<br>- DriverGroupId<br>- DriverGroupName\*\*<br><br>. |
| /Operator:`{Equal|NotEqual|GreaterOrEqual|LessOrEqual|Contains}` | Specifies the relationship between the attribute and the values. You can only specify **Contains** with string attributes. You can only specify **GreaterOrEqual** and **LessOrEqual** with date and version attributes. |
| /Value:`<Value>` | Specifies the value to search for relative to the specified `<attribute>`. You can specify multiple values for a single **/Filtertype**. The available values for each filter are:<br>- **PackageId** - Specify a valid GUID. For example: {4d36e972-e325-11ce-bfc1-08002be10318}<br>- **PackageName** - Specify any string value<br>- **PackageEnabled** - Specify **Yes** or **No**<br>- **Packagedateadded** - Specify the date in the following format: YYYY/MM/DD<br>- **PackageInfFilename** - Specify any string value<br>- **PackageClass** - Specify a valid class name or class GUID. For example: **DiskDrive**, **Net**, or {4d36e972-e325-11ce-bfc1-08002be10318}<br>- **PackageProvider** - Specify any string value<br>- **PackageArchitecture** - Specify **x86**, **x64**, or **ia64**<br>- **PackageLocale** - Specify a valid language identifier. For example: **en-US** or **es-ES**<br>- **PackageSigned** - Specify **Yes** or **No**<br>- **PackagedatePublished** - Specify the date in the following format: YYYY/MM/DD<br>- **Packageversion** - Specify the version in the following format: a.b.x.y. For example: 6.1.0.0<br>- **Driverdescription** - Specify any string value<br>- **DriverManufacturer** - Specify any string value<br>- **DriverHardwareId** - Specify any string value<br>- **DrivercompatibleId** - Specify any string value<br>- **DriverExcludeId** - Specify any string value<br>- **DriverGroupId** - Specify a valid GUID. For example: {4d36e972-e325-11ce-bfc1-08002be10318}<br>- **DriverGroupName** - Specify any string value<br><br> For more information about these values, see [Driver and Package attributes](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759262%28v=ws.11%29). |

## Examples

To add driver packages to a boot image, type one of the following:

```
wdsutil /add-ImageDriverPackagemedia:WinPE Boot Imagemediatype:Boot /Architecture:x86 /Filtertype:DriverGroupName /Operator:Equal /Value:x86Bus /Filtertype:PackageProvider /Operator:Contains /Value:Provider1 /Filtertype:Packageversion /Operator:GreaterOrEqual /Value:6.1.0.0
```

```
wdsutil /verbose /add-ImageDriverPackagemedia: WinPE Boot Image /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filtertype:PackageClass /Operator:Equal /Value:Net /Filtertype:DriverManufacturer /Operator:NotEqual /Value:Name1 /Value:Name2 /Filtertype:Packagedateadded /Operator:LessOrEqual /Value:2008/01/01
```

```
wdsutil /verbose /add-ImageDriverPackagemedia:WinPE Boot Image /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filtertype:PackageClass /Operator:Equal /Value:Net /Value:System /Value:DiskDrive /Value:HDC /Value:SCSIAdapter
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-imagedriverpackage command](wdsutil-add-imagedriverpackage)
- [wdsutil add-alldriverpackages command](wdsutil-add-alldriverpackages)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)