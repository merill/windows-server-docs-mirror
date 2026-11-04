---
layout: Conceptual
title: remove-DriverGroup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-remove-drivergroup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for remove-DriverGroup, which removes a driver group from a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: dfbfde60-09f0-ee86-1f97-d524eb1ec0bd
document_version_independent_id: 04faf643-3f08-f0bd-1ed0-59b118b3abde
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-remove-drivergroup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-remove-drivergroup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-remove-drivergroup.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a828d283-4a62-94e0-fa68-227e447ecf43
---

# remove-DriverGroup | Microsoft Learn

Removes a driver group from a server.

## Syntax

```
wdsutil /Remove-DriverGroup /DriverGroup:<Group Name> [/Server:<Server name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /DriverGroup:&lt;Group Name&gt; | Specifies the name of the driver group to remove. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If a server name is not specified, the local server is used. |

## Examples

To remove a driver group, type one of the following:

```
wdsutil /Remove-DriverGroup /DriverGroup:PrinterDrivers
```

```
wdsutil /Remove-DriverGroup /DriverGroup:PrinterDrivers /Server:MyWdsServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)