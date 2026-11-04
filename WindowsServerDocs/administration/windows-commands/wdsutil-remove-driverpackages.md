---
layout: Conceptual
title: wdsutil remove-driverpackages | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-remove-driverpackages
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil remove-driverpackages, which removes driver packages from the server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 15f4bd9f-c1ba-3741-7c3f-15cae4d3072f
document_version_independent_id: 053f2211-c18b-67fa-17b1-908036b4268b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-remove-driverpackages.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-remove-driverpackages
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-remove-driverpackages.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1e2eeac3-c163-a9eb-2809-a7cfebb7f7a2
---

# wdsutil remove-driverpackages | Microsoft Learn

Removes driver packages from the server.

## Syntax

```
wdsutil /remove-DriverPackages [/Server:<Server name>] /Filtertype:<Filter type> /Operator:{Equal | NotEqual | GreaterOrEqual | LessOrEqual | Contains} /Value:<Value> [/Value:<Value> ...]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server: &lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If a server name is not specified, the local server is used. |
| /Filtertype:&lt;Filter type&gt; | Specifies the attribute of the driver package to search for. You can specify multiple attributes in a single command. You must also specify **/Operator** and **/Value** with this option. &lt;Filter type&gt; can be one of the following:<br>- **PackageId**<br>- **PackageName**<br>- **PackageEnabled**<br>- **Packagedateadded**<br>- **PackageInfFilename**<br>- **PackageClass**<br>- **PackageProvider**<br>- **PackageArchitecture**<br>- **PackageLocale**<br>- **PackageSigned**<br>- **PackagedatePublished**<br>- **Packageversion**<br>- **Driverdescription**<br>- **DriverManufacturer**<br>- **DriverHardwareId**<br>- **DrivercompatibleId**<br>- **DriverExcludeId**<br>- **DriverGroupId**<br>- **DriverGroupName** |
| /Operator:{Equal | NotEqual | GreaterOrEqual | LessOrEqual | Contains} | Specifies the relationship between the attribute and the values. You can only specify **Contains** with string attributes. You can only specify **GreaterOrEqual** and **LessOrEqual** with date and version attributes. |
| /Value:&lt;Value&gt; | Specifies the value to search for the specified &lt;attribute&gt;. You can specify multiple values for a single **/Filtertype**. The following list outlines the attributes that you can specify for each filter. For more information about these attributes, see [Driver and Package attributes](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759262%28v=ws.11%29) (https://go.microsoft.com/fwlink/?LinkId=166895). <br>- PackageId - Specify a valid GUID. For example: {4d36e972-e325-11ce-bfc1-08002be10318}.<br>- PackageName - Specify any string value.<br>- PackageEnabled - Specify **Yes** or **No**.<br>- Packagedateadded - Specify the date in the following format: YYYY/MM/DD.<br>- PackageInfFilename - Specify any string value.<br>- PackageClass - Specify a valid class name or class GUID. For example: **DiskDrive**, **Net**, or {4d36e972-e325-11ce-bfc1-08002be10318}.<br>- PackageProvider - Specify any string value.<br>- PackageArchitecture - Specify **x86**, **x64**, or **ia64**.<br>- PckageLocale - Specify a valid language identifier. For example: **en-US** or **es-ES**.<br>- PackageSigned - Specify **Yes** or **No**.<br>- PackagedatePublished - Specify the date in the following format: YYYY/MM/DD.<br>- Packageversion - Specify the version in the following format: a.b.x.y. For example: 6.1.0.0.<br>- Driverdescription - Specify any string value.<br>- DriverManufacturer - Specify any string value.<br>- DriverHardwareId - Specify any string value.<br>- DrivercompatibleId - Specify any string value.<br>- DriverExcludeId - Specify any string value.<br>- DriverGroupId - Specify a valid GUID. For example: {4d36e972-e325-11ce-bfc1-08002be10318}.<br>- DriverGroupName - Specify any string value. |

## Examples

To remove packages, type one of the following:

```
wdsutil /verbose /remove-DriverPackages /Server:MyWdsServer
/Filtertype:PackageProvider /Operator:Equal /Value:Name1 /Value:Name2
```

```
wdsutil /remove-DriverPackages /Filtertype:PackageArchitecture /Operator:Equal
/Value:x86 /Value:x64 /Filtertype:PackageEnabled /Operator:Equal /Value:No
```

```
wdsutil /verbose /remove-DriverPackages /Server:MyWdsServer
/Filtertype:Packagedateadded /Operator:LessOrEqual /Value:2008/01/01
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil remove-driverpackage command](wdsutil-remove-driverpackage)