---
layout: Conceptual
title: Subcommand set-DriverGroupFilter | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-set-drivergroupfilter
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for Subcommand set-DriverGroupFilter, which adds or removes an existing driver group filter from a driver group.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f9315c90-2354-4c17-8d4b-a846208dd71c
document_version_independent_id: 615acbde-ac06-30f8-4eca-ce178c549bbf
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-set-drivergroupfilter.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-set-drivergroupfilter
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-set-drivergroupfilter.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 94c1d0be-6407-b75a-e6cb-10b360f77193
---

# Subcommand set-DriverGroupFilter | Microsoft Learn

Adds or removes an existing driver group filter from a driver group.

## Syntax

```
wdsutil /Set-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type> [/Policy:{Include | Exclude}] [/AddValue:<Value> [/AddValue:<Value> ...]] [/RemoveValue:<Value> [/RemoveValue:<Value> ...]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /DriverGroup:&lt;Group Name&gt; | Specifies the name of the driver group. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If a server name is not specified, the local server is used. |
| /FilterType:&lt;FilterType&gt; | Specifies the type of driver group filter to add or remove. You can specify multiple filters in a single command. For each **/FilterType**, you can add or remove multiple values using **/RemoveValue** and **/AddValue**. &lt;FilterType&gt; can be one of the following:**BiosVendor** **BiosVersion** **ChassisType** **Manufacturer** **Uuid** **OsVersion** **OsEdition** **OsLanguage** |
| [/Policy:{Include | Exclude}] |
| [/AddValue:&lt;Value&gt;] | Specifies the new client value to add to the filter. You can specify multiple values for a single filter type. See the following list for valid attribute values for **ChassisType**. For information about obtaining the values for all other filter types, see [Driver Group Filters](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759191%28v=ws.11%29) (https://go.microsoft.com/fwlink/?LinkID=155158).**Other** **UnknownChassis** **Desktop** **LowProfileDesktop** **PizzaBox** **MiniTower** **Tower** **Portable** **Laptop** **Notebook** **Handheld** **DockingStation** **AllInOne** **SubNotebook** **SpaceSaving** **LunchBox** **MainSystemChassis** **ExpansionChassis** **SubChassis** **BusExpansionChassis** **PeripheralChassis** **StorageChassis** **RackMountChassis** **SealedCaseComputer** **MultiSystemChassis** **CompactPci** **AdvancedTca** |
| [/RemoveValue:&lt;Value&gt;] | Specifies the existing client value to remove from the filter as specified with **/AddValue**. |

## Examples

To remove a filter, type one of the following:

```
wdsutil /Set-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /AddValue:Name1 /RemoveValue:Name2
```

```
wdsutil /Set-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /RemoveValue:Name1 /FilterType:ChassisType /Policy:Exclude /AddValue:Tower /AddValue:MiniTower
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)