---
layout: Conceptual
title: wdsutil delete-autoadddevices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-delete-autoadddevices
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil delete-autoadddevices command, which deletes computers that are pending, rejected, or approved from the Auto-add database.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e6b851c1-5d46-1564-94e4-9cad36595dc9
document_version_independent_id: c869a9ac-c283-4f98-e41b-a2a6ba7e471a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-delete-autoadddevices.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-delete-autoadddevices
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-delete-autoadddevices.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ae59ee21-addc-a491-138a-9207528fdb80
---

# wdsutil delete-autoadddevices | Microsoft Learn

Deletes computers that are pending, rejected, or approved from the auto-add database. This database stores information about these computers on the server.

## Syntax

```
wdsutil /delete-AutoaddDevices [/Server:<Servername>] /Devicetype:{PendingDevices | RejectedDevices |ApprovedDevices}
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:`<Servername>`] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| /Devicetype:`{PendingDevices|RejectedDevices|ApprovedDevices}` | Specifies the type of computer to delete from the database. This type can be **PendingDevices**, which returns all computers in the database that have a status of pending, **RejectedDevices**, which returns all computers in the database that have a status of rejected, or **ApprovedDevices**, which returns all computers that have a status of approved. |

## Examples

To delete all rejected computers, type:

```
wdsutil /delete-AutoaddDevices /Devicetype:RejectedDevices
```

To delete all approved computers, type:

```
wdsutil /verbose /delete-AutoaddDevices /Server:MyWDSServer /Devicetype:ApprovedDevices
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil approve-autoadddevices command](wdsutil-approve-autoadddevices)
- [wdsutil get-autoadddevices command](wdsutil-get-autoadddevices)
- [wdsutil reject-autoadddevices command](wdsutil-reject-autoadddevices)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)