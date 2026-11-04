---
layout: Conceptual
title: wdsutil add-drivergrouppackage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-add-drivergrouppackage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil add-drivergrouppackage command, which adds a driver package to a driver group.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 002d7afe-84c4-15c1-92d4-a7609cbdb372
document_version_independent_id: 58bc26d0-44d5-6218-d0e8-ecdc45807019
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-add-drivergrouppackage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-add-drivergrouppackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-add-drivergrouppackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 0a47e4e7-7f9d-6cf0-c4f4-d01d6de53045
---

# wdsutil add-drivergrouppackage | Microsoft Learn

Adds a driver package to a driver group.

## Syntax

```
wdsutil /add-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```

### Parameters

| Parameter | Description |
| --- | --- |
| /DriverGroup:`<Groupname>` | Specifies the name of the new driver group. |
| /Server:`<Servername>` | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If no server name is specified, the local server is used. |
| /DriverPackage:`<Name>` | Specifies the name of the driver package to be added to the group. You must specify this option if the driver package cannot be uniquely identified by name. |
| /PackageId:`<ID>` | Specifies the ID for a package. To find the Package ID, select the driver group that the package is in (or the **All Packages** node), right-click the package, and then select **Properties**. The Package ID is listed on the **General** tab, for example: **{DD098D20-1850-4fc8-8E35-EA24A1BEFF5E}**. |

## Examples

To add a driver group package, type either:

```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```

```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /DriverPackage:XYZ
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil add-drivergroupfilter command](wdsutil-add-drivergroupfilter)
- [wdsutil add-drivergrouppackages command](wdsutil-add-drivergrouppackages)
- [wdsutil add-drivergroup command](wdsutil-add-drivergroup)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)