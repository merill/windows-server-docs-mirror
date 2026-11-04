---
layout: Conceptual
title: wdsutil stop-transportserver | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-stop-transportserver
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for stop-TransportServer
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 88cf4e25-d7f8-7863-207f-eb555af4f3af
document_version_independent_id: 817dc880-1417-89eb-935f-09bb454b93de
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-stop-transportserver.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-stop-transportserver
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-stop-transportserver.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b2c207dd-0963-61c7-58aa-56c5a1b10ba2
---

# wdsutil stop-transportserver | Microsoft Learn

Stops all services on a Transport Server.

## Syntax

```
wdsutil [Options] /Stop-TransportServer [/Server:<Server name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the Transport Server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no Transport Server is specified, the local server will be used. |

## Examples

To stop the services, type one of the following:

```
wdsutil /Stop-TransportServer
wdsutil /verbose /Stop-TransportServer /Server:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil disable-transportserver command](wdsutil-disable-transportserver)
- [wdsutil enable-transportserver command](wdsutil-enable-transportserver)
- [wdsutil get-transportserver command](wdsutil-get-transportserver)
- [wdsutil set-transportserver command](wdsutil-set-transportserver)
- [wdsutil start-transportserver command](wdsutil-start-transportserver)