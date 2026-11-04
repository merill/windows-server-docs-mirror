---
layout: Conceptual
title: wdsutil start-transportserver | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-start-transportserver
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for Subcommand start-TransportServer, which starts all services for a Transport Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: ee767ffa-5f27-f42c-89c5-e5e17ca656a3
document_version_independent_id: aaf45693-0c86-8b62-73c7-ca06d4ad90a8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-start-transportserver.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-start-transportserver
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-start-transportserver.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c716d6e8-bfcf-ae1b-653a-2fd6d8b98018
---

# wdsutil start-transportserver | Microsoft Learn

Starts all services for a Transport Server.

## Syntax

```
wdsutil [Options] /start-TransportServer [/Server:<Server name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the Transport Server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |

## Examples

To start the server, type one of the following:

```
wdsutil /start-TransportServer
wdsutil /verbose /start-TransportServer /Server:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil disable-transportserver command](wdsutil-disable-transportserver)
- [wdsutil enable-transportserver command](wdsutil-enable-transportserver)
- [wdsutil get-transportserver command](wdsutil-get-transportserver)
- [wdsutil set-transportserver command](wdsutil-set-transportserver)
- [wdsutil stop-transportserver command](wdsutil-stop-transportserver)