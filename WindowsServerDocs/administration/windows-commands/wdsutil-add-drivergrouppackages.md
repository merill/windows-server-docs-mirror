---
layout: Conceptual
title: wdsutil add-drivergrouppackages | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-add-drivergrouppackages
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil add-drivergrouppackages command, which add driver group packages.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 80a4a257-2b13-b144-b7e9-1e87dc5dff79
document_version_independent_id: 6caa76e9-79dd-e302-c322-92876b4b3715
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-add-drivergrouppackages.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-add-drivergrouppackages
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-add-drivergrouppackages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: a52fba39-a544-4069-c3e9-f159b2bd853c
---

# wdsutil add-drivergrouppackages | Microsoft Learn

Adds driver group packages.

## Syntax

```
wdsutil /add-DriverGroupPackages /DriverGroup:<Group Name> [/Server:<Server Name>] /Filtertype:<Filter type> /Operator:{Equal | NotEqual | GreaterOrEqual | LessOrEqual | Contains} /Value:<Value> [/Value:<Value>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /DriverGroup:`<Groupname>` | Specifies the name of the new driver group. |
| /Server:`<Servername>` | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If no server name is specified, the local server is used. |
| /Filtertype:`<Filtertype>` | Specifies the type of the driver package to search for. You can specify multiple attributes in a single command. You must also specify **/Operator** and **/Value** with this option. Valid values include:<br>- PackageId<br>- PackageName<br>- PackageEnabled<br>- Packagedateadded<br>- PackageInfFilename<br>- PackageClass<br>    PackageProvider<br>- PackageArchitecture<br>- PackageLocale<br>- PackageSigned<br>- PackagedatePublished<br>- Packageversion<br>- Driverdescription<br>- DriverManufacturer<br>- DriverHardwareId<br>- DrivercompatibleId<br>- DriverExcludeId<br>- DriverGroupId<br>- DriverGroupName\*\*<br><br>. |
| /Operator:`{Equal|NotEqual|GreaterOrEqual|LessOrEqual|Contains}` | Specifies the relationship between the attribute and the values. You can only specify **Contains** with string attributes. You can only specify **Equal**, **NotEqual**, **GreaterOrEqual** and **LessOrEqual** with date and version attributes. |
| /Value:`<Value>` | Specifies the client value corresponding to **/Filtertype**. You can specify multiple values for a single **/Filtertype**. The available values for each filter are:<br>- **PackageId** - Specify a valid GUID. For example: {4d36e972-e325-11ce-bfc1-08002be10318}<br>- **PackageName** - Specify any string value<br>- **PackageEnabled** - Specify **Yes** or **No**<br>- **Packagedateadded** - Specify the date in the following format: YYYY/MM/DD<br>- **PackageInfFilename** - Specify any string value<br>- **PackageClass** - Specify a valid class name or class GUID. For example: **DiskDrive**, **Net**, or {4d36e972-e325-11ce-bfc1-08002be10318}<br>- **PackageProvider** - Specify any string value<br>- **PackageArchitecture** - Specify **x86**, **x64**, or **ia64**<br>- **PackageLocale** - Specify a valid language identifier. For example: **en-US** or **es-ES**<br>- **PackageSigned** - Specify **Yes** or **No**<br>- **PackagedatePublished** - Specify the date in the following format: YYYY/MM/DD<br>- **Packageversion** - Specify the version in the following format: a.b.x.y. For example: 6.1.0.0<br>- **Driverdescription** - Specify any string value<br>- **DriverManufacturer** - Specify any string value<br>- **DriverHardwareId** - Specify any string value<br>- **DrivercompatibleId** - Specify any string value<br>- **DriverExcludeId** - Specify any string value<br>- **DriverGroupId** - Specify a valid GUID. For example: {4d36e972-e325-11ce-bfc1-08002be10318}<br>- **DriverGroupName** - Specify any string value<br><br> For more information about these values, see [Driver and Package attributes](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759262%28v=ws.11%29). |

## Examples

To add a driver group package, type either:

```
wdsutil /verbose /add-DriverGroupPackages /DriverGroup:printerdrivers /Filtertype:PackageClass /Operator:Equal /Value:printer /Filtertype:DriverManufacturer /Operator:NotEqual /Value:Name1 /Value:Name2
```

```
wdsutil /verbose /add-DriverGroupPackages /DriverGroup:DisplayDriversX86 /Filtertype:PackageClass /Operator:Equal /Value:Display /Filtertype:PackageArchitecture /Operator:Equal /Value:x86 /Filtertype:Packagedateadded /Operator:LessOrEqual /Value:2008/01/01
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-driverpackage command](wdsutil-add-driverpackage)
- [wdsutil add-drivergrouppackage command](wdsutil-add-drivergrouppackage)
- [wdsutil add-alldriverpackages command](wdsutil-add-alldriverpackages)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)