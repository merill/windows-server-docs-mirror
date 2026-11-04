---
layout: Conceptual
title: wdsutil disable-transportserver | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-disable-transportserver
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil disable-transportserver command, which disables all services for a Transport Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ca259d22-2878-1463-e652-0604b189db1c
document_version_independent_id: 6526f44e-63e5-b94d-d1aa-3e1b8557e579
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-disable-transportserver.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-disable-transportserver
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-disable-transportserver.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 129113b3-5ffd-eb3e-2421-665ffdd16a02
---

# wdsutil disable-transportserver | Microsoft Learn

Disables all services for a Transport Server.

## Syntax

```
wdsutil [Options] /Disable-TransportServer [/Server:<Servername>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:`<Servername>`] | Specifies the name of the Transport Server to be disabled. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no Transport Server name is specified, the local server will be used. |

## Examples

To disable the server, type either:

```
wdsutil /Disable-TransportServer
```

```
wdsutil /verbose /Disable-TransportServer /Server:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil enable-transportserver command](wdsutil-enable-transportserver)
- [wdsutil get-transportserver command](wdsutil-get-transportserver)
- [wdsutil set-transportserver command](wdsutil-set-transportserver)
- [wdsutil start-transportserver command](wdsutil-start-transportserver)
- [wdsutil stop-transportserver command](wdsutil-stop-transportserver)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)