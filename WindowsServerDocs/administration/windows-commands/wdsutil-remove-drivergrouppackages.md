---
layout: Conceptual
title: wdsutil remove-drivergrouppackages | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-remove-drivergrouppackages
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil remove-drivergrouppackages, which removes driver packages from a driver group on a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 5d6643cb-5cec-6db6-47bf-3e189b9ceb5b
document_version_independent_id: 79d78922-d735-927d-1c75-db3f9c2747cb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-remove-drivergrouppackages.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-remove-drivergrouppackages
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-remove-drivergrouppackages.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c722d231-a9d9-e7d9-bcde-6fde67eb5cb0
---

# wdsutil remove-drivergrouppackages | Microsoft Learn

Removes driver packages from a driver group on a server.

## Syntax

```
wdsutil /remove-DriverGroupPackages /DriverGroup:<Group Name> [/Server:<Server Name>] /Filtertype:<Filter type> /Operator:{Equal | NotEqual | GreaterOrEqual | LessOrEqual | Contains} /Value:<Value> [/Value:<Value> ...]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /DriverGroup:&lt;Group Name&gt; | Specifies the name of the driver group. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If a server name is not specified, the local server is used. |
| /Filtertype:&lt;Filter type&gt; | Specifies the attribute of the driver package to search for. You can specify multiple attributes in a single command. You must also specify **/Operator** and **/Value** with this option.<br>&lt;Filter type&gt; can be one of the following:<br><br>**PackageId**<br><br>**PackageName**<br><br>**PackageEnabled**<br><br>**Packagedateadded**<br><br>**PackageInfFilename**<br><br>**PackageClass**<br><br>**PackageProvider**<br><br>**PackageArchitecture**<br><br>**PackageLocale**<br><br>**PackageSigned**<br><br>**PackagedatePublished**<br><br>**Packageversion**<br><br>**Driverdescription**<br><br>**DriverManufacturer**<br><br>**DriverHardwareId**<br><br>**DrivercompatibleId**<br><br>**DriverExcludeId**<br><br>**DriverGroupId**<br><br>**DriverGroupName** |
| /Operator:{Equal | NotEqual | GreaterOrEqual | LessOrEqual | Contains} | Specifies the relationship between the attribute and the values. You can only specify **Contains** with string attributes. You can only specify **GreaterOrEqual** and **LessOrEqual** with date and version attributes. |
| /Value:&lt;Value&gt; | Specifies the value to search for the specified &lt;attribute&gt;. You can specify multiple values for a single **/Filtertype**. The following list outlines the attributes that you can specify for each filter. For more information about these attributes, see [Driver and Package attributes](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759262%28v=ws.11%29) (https://go.microsoft.com/fwlink/?LinkId=166895).<br>- PackageId - Specify a valid GUID. For example: {4d36e972-e325-11ce-bfc1-08002be10318}.- PackageName Specify any string value.- PackageEnabled - Specify **Yes** or **No**.- Packagedateadded - Specify the date in the following format: YYYY/MM/DD- PackageInfFilename Specify any string value.- PackageClass - Specify a valid class name or class GUID. For example: **DiskDrive**, **Net**, or {4d36e972-e325-11ce-bfc1-08002be10318}.- PackageProvider Specify any string value.- PackageArchitecture - Specify **x86**, **x64**, or **ia64**.- PckageLocale - Specify a valid language identifier. For example: **en-US** or **es-ES**.- PackageSigned - Specify **Yes** or **No**.- PackagedatePublished - Specify the date in the following format: YYYY/MM/DD- Packageversion - Specify the version in the following format: a.b.x.y. For example: 6.1.0.0- Driverdescription Specify any string value.- DriverManufacturer Specify any string value.- DriverHardwareId - Specify any string value.- DrivercompatibleId - Specify any string value.- DriverExcludeId - Specify any string value.- DriverGroupId - Specify a valid GUID. For example: {4d36e972-e325-11ce-bfc1-08002be10318}.- DriverGroupName Specify any string value. |

## Examples

To remove driver packages from a driver group, type one of the following:

```
wdsutil /verbose /remove-DriverGroupPackages /DriverGroup:printerdrivers
/Filtertype:DriverManufacturer /Operator:NotEqual /Value:Name1 /Value:Name2
```

```
wdsutil /verbose /remove-DriverGroupPackages /DriverGroup:DisplayDrivers
/Filtertype:PackageArchitecture /Operator:Equal /Value:x86
/Filtertype:Packagedateadded /Operator:LessOrEqual /Value:2008/01/01
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil remove-drivergrouppackage command](wdsutil-remove-drivergrouppackage)