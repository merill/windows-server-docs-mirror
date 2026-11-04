---
layout: Conceptual
title: wdsutil get-autoadddevices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-autoadddevices
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get-autoadddevices, which displays all computers that are in the Auto-add database on a Windows Deployment Services server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a9018dc0-f0ab-b6cd-66e9-167e2c621148
document_version_independent_id: a145291d-e090-c80c-7914-e7cff3599670
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-autoadddevices.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-autoadddevices
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-autoadddevices.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: bfe4fe1d-c8f5-1b1c-dae8-1caa29d40407
---

# wdsutil get-autoadddevices | Microsoft Learn

Displays all computers that are in the Auto-add database on a Windows Deployment Services server.

## Syntax

```
wdsutil [Options] /Get-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices | ApprovedDevices}
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| /Devicetype:{PendingDevices | RejectedDevices | ApprovedDevices} | Specifies the type of computer to return.<br>- **PendingDevices** returns all computers in the database that have a status of pending.- **RejectedDevices** returns all computers in the database that have a status of rejected.- **ApprovedDevices** returns all computers in the database that have a status of approved. |

## Examples

To see all of the approved computers, type:

```
wdsutil /Get-AutoaddDevices /Devicetype:ApprovedDevices
```

To see all of the rejected computers, type:

```
wdsutil /verbose /Get-AutoaddDevices /Devicetype:RejectedDevices /Server:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil delete-autoadddevices command](wdsutil-delete-autoadddevices)
- [wdsutil approve-autoadddevices command](wdsutil-approve-autoadddevices)
- [wdsutil reject-autoadddevices command](wdsutil-reject-autoadddevices)