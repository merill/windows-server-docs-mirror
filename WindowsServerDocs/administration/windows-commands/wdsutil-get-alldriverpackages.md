---
layout: Conceptual
title: wdsutil get-alldriverpackages | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-alldriverpackages
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil get-alldriverpackages command, which displays information about all the driver packages on a server that match the specified search criteria.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a5966d8d-dc3d-3ec3-f55b-702194b3567d
document_version_independent_id: daedf08d-2231-77af-0f05-32a972f52571
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-alldriverpackages.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-alldriverpackages
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-alldriverpackages.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 33e14485-cd6b-1f8f-ed8a-d9876f96c28d
---

# wdsutil get-alldriverpackages | Microsoft Learn

Displays information about all the driver packages on a server that match the specified search criteria.

## Syntax

```
wdsutil /get-alldriverpackages [/server:<servername>] [/show:{drivers | files | all}] [/filtertype:<filtertype> /operator:{equal | notequal | greaterorequal | lessorequal | contains} /value:<value> [/value:<value> ...]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[/server:<servername>] ` | The name of the server. This can be the NetBIOS name or the FQDN. If a server name isn't specified, the local server is used. |
| `[/show:{drivers | files | all}]` | Indicates the package information to display. If **/show** isn't specified, the default is to return only the driver package metadata. **Drivers** displays the list of drivers in the package, **files** displays the list of files in the package, and **all** displays drivers and files. |
| `/filtertype:<filtertype>` | Specifies the attribute of the driver package to search for. You can specify multiple attributes in a single command. You must also specify **/operator** and **/value** with this option.<br>The `<filtertype>` can be one of the following:<br><br>- PackageId<br>- PackageName<br>- PackageEnabled<br>- Packagedateadded<br>- PackageInfFilename<br>- PackageClass<br>- PackageProvider<br>- PackageArchitecture<br>- PackageLocale<br>- PackageSigned<br>- PackagedatePublished<br>- Packageversion<br>- Driverdescription<br>- DriverManufacturer<br>- DriverHardwareId<br>- DrivercompatibleId<br>- DriverGroupId<br>- DriverGroupName |
| `/operator:{equal | notequal | greaterorequal | lessorequal | contains}` | Specifies the relationship between the attribute and the values. You can specify **contains** only with string attributes. You can specify **greaterorequal** and **lessorequal** only with date and version attributes. |
| `/value:<value>` | Specifies the value to search on for the specified `<attribute>`. You can specify multiple values for a single **/filtertype**. The list below outlines the attributes you can specify for each filter. For more information about these attributes, see [Driver and Package attributes](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759262%28v=ws.11%29). The attributes can include:<br>- **PackageId.** Specifies a valid GUID. For example:{4d36e972-e325-11ce-bfc1-08002be10318}.<br>- **PackageName.** Specifies any string value.<br>- **PackageEnabled.** Specifies *Yes* or *No*.<br>- **Packagedateadded.** Specifies the date in the following format: YYYY/MM/DD<br>- **PackageInfFilename.** Specifies any string value.<br>- **PackageClass.** Specifies a valid class name or class GUID. For example: *DiskDrive*, *Net*, or *{4d36e972-e325-11ce-bfc1-08002be10318}*.<br>- **PackageProvider.** Specifies any string value.<br>- **PackageArchitecture.** Specifies *x86*, *x64*, or *ia64*.<br>- **PackagLocale.** Specifies a valid language identifier. For example: *en-US* or *es-ES*.<br>- **PackageSigned.** Specifies **Yes** or **No**.<br>- **PackagedatePublished.** Specifies the date in the following format: YYYY/MM/DD.<br>- **Packageversion.** Specifies the version in the following format: a.b.x.y. For example: 6.1.0.0.<br>- **Driverdescription.** Specifies any string value.<br>- **DriverManufacturer.** Specifies any string value.<br>- **DriverHardwareId.** Specifies any string value.<br>- **DrivercompatibleId.** Specifies any string value.<br>- **DriverExcludeId.** Specifies any string value.<br>- **DriverGroupId.** Specifies a valid GUID. For example: {4d36e972-e325-11ce-bfc1-08002be10318}.<br>- **DriverGroupName.** Specifies any string value. |

## Examples

To display information, type either:

```
wdsutil /get-alldriverpackages /server:MyWdsServer /show:all /filtertype:drivergroupname /operator:contains /value:printer /filtertype:packagearchitecture /operator:equal /value:x64 /value:x86
```

```
wdsutil /get-alldriverpackages /show:drivers /filtertype:packagedateadded /operator:greaterorequal /value:2008/01/01
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-driverpackage command](wdsutil-get-driverpackage)
- [wdsutil get-driverpackagefile command](wdsutil-get-driverpackagefile)