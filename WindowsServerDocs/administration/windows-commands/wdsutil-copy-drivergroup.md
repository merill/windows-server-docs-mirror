---
layout: Conceptual
title: copy-drivergroup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-copy-drivergroup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the copy-drivergroup command, which duplicates an existing driver group on the server including the filters, driver packages, and enabled/disabled status.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9b79a657-b716-ae1d-92a8-6e344499c98a
document_version_independent_id: 3753a34c-d0af-e79f-9128-52778cb2fb1d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-copy-drivergroup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-copy-drivergroup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-copy-drivergroup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 8b17044a-b0b4-0ce9-5b40-f418bd3e844c
---

# copy-drivergroup | Microsoft Learn

Duplicates an existing driver group on the server including the filters, driver packages, and enabled/disabled status.

## Syntax

```
wdsutil /Copy-DriverGroup [/Server:<Server name>] /DriverGroup:<Source Groupname> /GroupName:<New Groupname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| /Server:`<Servername>` | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If no server name is specified, the local server is used. |
| /DriverGroup:`<Source Groupname>` | Specifies the name of the source driver group. |
| /GroupName:`<New Groupname>` | Specifies the name of the new driver group. |

## Examples

To copy a driver group, type either:

```
wdsutil /Copy-DriverGroup /Server:MyWdsServer /DriverGroup:PrinterDrivers /GroupName:X86PrinterDrivers
```

```
wdsutil /Copy-DriverGroup /DriverGroup:PrinterDrivers /GroupName:ColorPrinterDrivers
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)