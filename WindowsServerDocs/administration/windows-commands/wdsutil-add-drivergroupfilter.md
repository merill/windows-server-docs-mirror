---
layout: Conceptual
title: add-DriverGroupFilter | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-add-drivergroupfilter
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the add-DriverGroupFilter command, which adds a filter to a driver group on a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9935096e-31c8-4c46-1c51-108ca0fc6b87
document_version_independent_id: 36a8a81d-51e0-e9a4-5a8c-81e251d9ddeb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-add-drivergroupfilter.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-add-drivergroupfilter
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-add-drivergroupfilter.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d2df62d2-c978-b947-17e9-f2251c2761ef
---

# add-DriverGroupFilter | Microsoft Learn

Adds a filter to a driver group on a server.

## Syntax

```
wdsutil /Add-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type> /Policy:{Include | Exclude} /Value:<Value> [/Value:<Value> ...]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /DriverGroup:`<Groupname>` | Specifies the name of the new driver group. |
| /Server:`<Servername>` | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If no server name is specified, the local server is used. |
| /Filtertype:`<Filtertype>` | Specifies the type of the filter to add to the group. You can specify multiple filter types in a single command. Each filter type must be followed by **/Policy** and at least one **/Value**. Valid values include:<br>- BiosVendor<br>- Biosversion<br>- Chassistype<br>- Manufacturer<br>- Uuid<br>- Osversion<br>- Osedition<br>- OsLanguage<br><br> For information about getting values for all other filter types, see [Driver Group Filters](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759191%28v=ws.11%29). |
| [/Policy:`{Include|Exclude}`] | Specifies the policy to be set on the filter. If **/Policy** is set to **Include**, client computers that match the filter are allowed to install the drivers in this group. If **/Policy** is set to **Exclude**, then client computers that match the filter are not allowed to install the drivers in this group. |
| [/Value:`<Value>`] | Specifies the client value that corresponds to **/Filtertype**. You can specify multiple values for a single type. For information about acceptable filter type values, see [Driver Group Filters](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759191%28v=ws.11%29). |

## Examples

To add a filter to a driver group, type either:

```
wdsutil /Add-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /Value:Name1 /Value:Name2
```

```
wdsutil /Add-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /Value:Name1 /FilterType:ChassisType /Policy:Exclude /Value:Tower /Value:MiniTower
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-drivergrouppackage command](wdsutil-add-drivergrouppackage)
- [wdsutil add-drivergrouppackages command](wdsutil-add-drivergrouppackages)
- [wdsutil add-drivergroup command](wdsutil-add-drivergroup)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)