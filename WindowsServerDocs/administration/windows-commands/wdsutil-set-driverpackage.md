---
layout: Conceptual
title: Subcommand set-DriverPackage | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-set-driverpackage
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for Subcommand set-DriverPackage, which renames and/or enables or disables a driver package on a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e9a3da10-e405-0f0a-d702-7f77e09ee2f9
document_version_independent_id: 33859e39-3286-7a09-402b-859965dfbf14
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-set-driverpackage.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-set-driverpackage
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-set-driverpackage.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 66f6c040-55ef-cfff-d82a-9e5bc17dc72e
---

# Subcommand set-DriverPackage | Microsoft Learn

Renames and/or enables or disables a driver package on a server.

## Syntax

```
wdsutil /Set-DriverPackage [/Server:<Server name>] {/DriverPackage:<Name> | /PackageId:<ID>} [/Name:<New Name>] [/Enabled:{Yes | No}
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the FQDN. If a server name is not specified, the local server is used. |
| [/DriverPackage:&lt;Name&gt;] | Specifies the current name of the driver package to modify. |
| [/PackageId:&lt;ID&gt;] | Specifies the Windows Deployment Services ID of the driver package. You must specify this option if the driver package cannot be uniquely identified by name. To find this ID for a package, click the driver group that the package is in (or the **All Packages** node), right-click the package, and then click **Properties**. The Package ID is listed on the **General** tab. For example: {DD098D20-1850-4FC8-8E35-EA24A1BEFF5E}. |
| [/Name:&lt;New Name&gt;] | Specifies the new name for the driver package. |
| [/Enabled:{Yes | No} |

## Examples

To change settings about a package, type one of the following:

```
wdsutil /Set-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318} /Name:MyDriverPackage
```

```
wdsutil /Set-DriverPackage /DriverPackage:MyDriverPackage /Name:NewName /Enabled:Yes
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)