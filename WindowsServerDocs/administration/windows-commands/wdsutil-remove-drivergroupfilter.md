---
layout: Conceptual
title: remove-DriverGroupFilter | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-remove-drivergroupfilter
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for remove-DriverGroupFilter, which removes a filter rule from a driver group on a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e7a89ccd-1d92-f835-f6e5-d563976a46d5
document_version_independent_id: d23ff0cc-bec5-eaf4-279a-a762f7601bfc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-remove-drivergroupfilter.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-remove-drivergroupfilter
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-remove-drivergroupfilter.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ece8d1bb-3396-e202-d11e-cbdef8c85628
---

# remove-DriverGroupFilter | Microsoft Learn

Removes a filter rule from a driver group on a server.

## Syntax

```
wdsutil /Remove-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type>
```

### Parameters

| Parameter | Description |
| --- | --- |
| /DriverGroup:&lt;Group Name&gt; | Specifies the name of the driver group. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If a server name is not specified, the local server is used. |
| [/FilterType:&lt;FilterType&gt;] | Specifies the type of the filter to remove from the group. &lt;FilterType&gt; can be one of the following:**BiosVendor** **BiosVersion** **ChassisType** **Manufacturer** **Uuid** **OsVersion** **OsEdition** **OsLanguage** |

## Examples

To remove a filter, type one of the following:

```
wdsutil /Remove-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer
```

```
wdsutil /Remove-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /FilterType:OSLanguage
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)