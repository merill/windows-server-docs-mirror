---
layout: Conceptual
title: wdsutil reject-autoadddevices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-reject-autoadddevices
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil reject-autoadddevices, which rejects computers that are pending administrative approval.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 721a5f1d-916e-52a8-28d2-b62a626c72f8
document_version_independent_id: 2a9d8b55-9b34-109b-a38c-786fc3cc4d7e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-reject-autoadddevices.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-reject-autoadddevices
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-reject-autoadddevices.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c81d0a75-226d-a2d0-6b00-8dd45ea527ad
---

# wdsutil reject-autoadddevices | Microsoft Learn

Rejects computers that are pending administrative approval. When the Auto-add policy is enabled, administrative approval is required before unknown computers (those that are not prestaged) can install an image. You can enable this policy using the **PXE Response** tab of the server s properties page.

## Syntax

```
wdsutil [Options] /Reject-AutoaddDevices [/Server:<Server name>] /RequestId:<Request ID or ALL>
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| /RequestId:&lt;Request ID | ALL&gt; | Specifies the request ID assigned to the pending computer. To reject all pending computers, specify **ALL**. |

## Examples

To reject a single computer, type:

```
wdsutil /Reject-AutoaddDevices /RequestId:12
```

To reject all computers, type:

```
wdsutil /verbose /Reject-AutoaddDevices /Server:MyWDSServer /RequestId:ALL
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil approve-autoadddevices command](wdsutil-approve-autoadddevices)
- [wdsutil delete-autoadddevices command](wdsutil-delete-autoadddevices)
- [wdsutil get-autoadddevices command](wdsutil-get-autoadddevices)