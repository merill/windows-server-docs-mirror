---
layout: Conceptual
title: Subcommand set-DriverGroup | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-set-drivergroup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for Subcommand set-DriverGroup, which sets the properties of an existing driver group on a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 5928a670-3239-271f-51f3-7c1890110eff
document_version_independent_id: ead85a92-9b34-d668-df1e-e96c83d4932a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-set-drivergroup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-set-drivergroup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-set-drivergroup.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0ef6a2c3-a92b-9824-9ada-2e95057bbc39
---

# Subcommand set-DriverGroup | Microsoft Learn

Sets the properties of an existing driver group on a server.

## Syntax

```
wdsutil /Set-DriverGroup /DriverGroup:<Group Name> [/Server:<Server Name>] [/Name:<New Group Name>] [/Enabled:{Yes | No}] [/Applicability:{Matched | All}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /DriverGroup:&lt;Group Name&gt; | Specifies the name of the driver group. |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If a server name is not specified, the local server is used. |
| [/Name:&lt;New Group Name&gt;] | Specifies the new name for the driver group. |
| [/Enabled:{Yes | No} | Enables or disables the driver group. |
| [/Applicability:{Matched | All}] | Specifies which packages to install if the filter criteria is met. **Matched** means install only the driver packages that match a client s hardware. **All** means install all packages to clients regardless of their hardware. |

## Examples

To set the properties for a driver group, type one of the following:

```
wdsutil /Set-DriverGroup /DriverGroup:printerdrivers /Enabled:Yes
```

```
wdsutil /Set-DriverGroup /DriverGroup:printerdrivers /Name:colorprinterdrivers /Applicability:All
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)[Subcommand: set-DriverGroupFilter](wdsutil-set-drivergroupfilter)